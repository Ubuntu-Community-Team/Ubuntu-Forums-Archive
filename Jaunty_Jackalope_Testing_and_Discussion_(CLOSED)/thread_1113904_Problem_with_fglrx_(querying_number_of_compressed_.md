---
title: "Problem with fglrx (querying number of compressed texture formats) - please verify"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Eremit on 2009-04-02
Hi,

I have a problem with

```

int numFormats;
glGetIntegerv(GL_NUM_COMPRESSED_TEXTURE_FORMATS_ARB, &numFormats);
printf("Number of compressed texture formats: %d\n", numFormats);

```

giving me "0" formats. I think it should be at least 5.

Could someone please verify this.

I suggest downloading this sample code:
[http://nehe.gamedev.net/data/lessons/linux/lesson02.tar.gz](http://nehe.gamedev.net/data/lessons/linux/lesson02.tar.gz)

and inserting the 3 lines of code above into
```
/* general OpenGL initialization function */
int initGL( GLvoid )
{
  ...
```

then calling
```
make
./lesson02
```

My card: Radeon HD4850

---

