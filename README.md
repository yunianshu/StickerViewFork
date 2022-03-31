# StickerViewFork
 贴图、文字气泡

fork:https://github.com/wuapnjie/StickerView


TextDrawable源码地址:

https://github.com/amulyakhare/TextDrawable

使用
####1. Create simple tile:



<ImageView android:layout_width="60dp"
android:layout_height="60dp"
android:id="@+id/image_view"/>
Note: Specify width/height for the ImageView and the drawable will auto-scale to fit the size.

TextDrawable drawable = TextDrawable.builder()
.buildRect("A", Color.RED);

ImageView image = (ImageView) findViewById(R.id.image_view);
image.setImageDrawable(drawable);
####2. Create rounded corner or circular tiles:



TextDrawable drawable1 = TextDrawable.builder()
.buildRoundRect("A", Color.RED, 10); // radius in px

TextDrawable drawable2 = TextDrawable.builder()
.buildRound("A", Color.RED);
####3. Add border:



TextDrawable drawable = TextDrawable.builder()
.beginConfig()
.withBorder(4) /* thickness in px */
.endConfig()
.buildRoundRect("A", Color.RED, 10);
####4. Modify font style:

TextDrawable drawable = TextDrawable.builder()
.beginConfig()
.textColor(Color.BLACK)
.useFont(Typeface.DEFAULT)
.fontSize(30) /* size in px */
.bold()
.toUpperCase()
.endConfig()
.buildRect("a", Color.RED)
####5. Built-in color generator:

ColorGenerator generator = ColorGenerator.MATERIAL; // or use DEFAULT
// generate random color
int color1 = generator.getRandomColor();
// generate color based on a key (same key returns the same color), useful for list/grid views
int color2 = generator.getColor("user@gmail.com")

// declare the builder object once.
TextDrawable.IBuilder builder = TextDrawable.builder()
.beginConfig()
.withBorder(4)
.endConfig()
.rect();

// reuse the builder specs to create multiple drawables
TextDrawable ic1 = builder.build("A", color1);
TextDrawable ic2 = builder.build("B", color2);
####6. Specify the width / height:

<ImageView android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:id="@+id/image_view"/>
Note: The ImageView could use wrap_content width/height. You could set the width/height of the drawable using code.

TextDrawable drawable = TextDrawable.builder()
.beginConfig()
.width(60)  // width in px
.height(60) // height in px
.endConfig()
.buildRect("A", Color.RED);

ImageView image = (ImageView) findViewById(R.id.image_view);
image.setImageDrawable(drawable);
####7. Other features:

Mix-match with other drawables. Use it in conjunction with LayerDrawable, InsetDrawable, AnimationDrawable, TransitionDrawable etc.

Compatible with other views (not just ImageView). Use it as background drawable, compound drawable for TextView, Button etc.

Use multiple letters or unicode characters to create interesting tiles.


