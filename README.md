# CTModExamples
Examples for giving your clustertruck trucks custom colours!

## Basic Colours
These are the basic named colours you can use:
- black
- blue
- clear
- cyan
- green
- grey
- magenta
- red
- white
- yellow

## Advanced Colours
### Hue examples with 15 degree intervals:
Hue Angle | Colour | Corresponding H
----------|--------|----------------
0° | red | 0.000f or 1.000f
15°	|	orange red | 0.042f
30° | orange | 0.083f
45° | khaki | 0.125f
60° | yellow | 0.167f
75° | lime | 0.208f
90° | olive | 0.250f
105° | grass green | 0.292f
120° | green | 0.333f
135° | bluish green | 0.375f
150° | teal | 0.417f
165° | greenish cyan | 0.458f
180° | cyan | 0.500f
195° | bluish cyan | 0.542f
210° | blue | 0.583f
225° | blue violet | 0.625f
240° | violet | 0.667f
255° | purple violet | 0.708f
270° | purple | 0.750f
285° | purple magenta | 0.792f
300° | magenta | 0.833f
315° | crimson | 0.875f
330° | scarlet | 0.917f
345° | scarlet red | 0.958f
360° | red | 1.000f or 0.000f

### Saturation (s) in relation to Value (v)
v\s | 0.00s | 0.33s | 0.66s | 1.00s
--|-------|-------|-------|------ 
0.00v | ![0, 0](https://i.imgur.com/ru4SsbE.png) | ![0, 33](https://i.imgur.com/ru4SsbE.png) | ![0, 66](https://i.imgur.com/ru4SsbE.png) | ![0, 1](https://i.imgur.com/ru4SsbE.png)
0.33v | ![33, 0](https://i.imgur.com/LnK5EdV.png) | ![33, 33](https://i.imgur.com/toDYdS1.png) | ![33, 66](https://i.imgur.com/1owqERT.png) | ![33, 1](https://i.imgur.com/lxshOpt.png)
0.66v | ![66, 0](https://i.imgur.com/vsiFcwq.png) | ![66, 33](https://i.imgur.com/VlUnMC8.png) | ![66, 66](https://i.imgur.com/Ge6VN6M.png) | ![66, 1](https://i.imgur.com/shclSa4.png)
1.00v | ![1, 0](https://i.imgur.com/qMg92kt.png) | ![1, 33](https://i.imgur.com/Thtbj2z.png) | ![1, 66](https://i.imgur.com/lmVLZXh.png) | ![1, 1](https://i.imgur.com/wtgvQeW.png)

## Colour Loops
### Examples
#### Rainbow loop
```Csharp
// in Update()
float h = Mathf.Repeat(Time.time / 2, 1f);
this.mTruckMaterial.color = Color.HSVToRGB(h, 0.5f, 0.8f);
```
#### Random Colour Loop
```Csharp
// in Update()
if (Mathf.Repeat(Time.time, 1f) + Time.deltaTime >= 1f) {
	this.mTruckMaterial.color = Color.HSVToRGB(UnityEngine.Random.Range(0f, 1f), 0.5f, 0.8f);
}
```
#### Orange Colour Pulse
```Csharp
// in Update()
float s = (Mathf.Sin(Time.time * 3) + 1f) / 2f;
this.mTruckMaterial.color = Color.HSVToRGB(0.083f, s, 0.8f);
```
#### Trans flag sirens
This was supposed to be a gradient but it kinda looks like police sirens so now it's trans flag sirens 😎.
```Csharp
// in Update()
Color[] colors = new Color[]	{
  Color.HSVToRGB(0.542f, 0.66f, 0.98f),
  Color.HSVToRGB(0.958f, 0.31f, 0.96f),
  Color.white,
  Color.HSVToRGB(0.958f, 0.31f, 0.96f),
  Color.HSVToRGB(0.542f, 0.66f, 0.98f)
};
float scaledTime = Mathf.Repeat(Time.time / 3f, 1f) * (float)(colors.Length - 1);
Color color = colors[(int)scaledTime];
Color color2 = colors[(int)(scaledTime + 1f)];
this.mTruckMaterial.color = Color.Lerp(color, color2, scaledTime - Mathf.Floor(scaledTime));
```
