---
title: "GLUT linking for OpenGL"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by svenskmand on 2008-08-09
Hello Everyone,

I have a problem with compiling a simple OpenGL example. I have installet GLUT with the commands:

```

sudo apt-get install glutg3 libglut3 libgl1-mesa-glx

```

and then i compile this simple example (notice that this program had compiled before I upgraded to Hardy 8.04) with the commandline:

```

gcc OpenGL.c -o test -lglut

```

the example code is:

```

#include <GL/gl.h>    // /usr/include/GL/gl.h
#include <GL/glut.h>  // /usr/include/GL/glut.h

// Compiles with "gcc OpenGL.c -o test -lglut" on linux

void display(void)
{
/*  clear all pixels  */
    glClear (GL_COLOR_BUFFER_BIT);

/*  draw white polygon (rectangle) with corners at
 *  (0.25, 0.25, 0.0) and (0.75, 0.75, 0.0)  
 */
    glColor3f (1.0, 1.0, 1.0);
    glBegin(GL_POLYGON);
        glVertex3f (0.25, 0.25, 0.0);
        glVertex3f (0.75, 0.25, 0.0);
        glVertex3f (0.75, 0.75, 0.0);
        glVertex3f (0.25, 0.75, 0.0);
    glEnd();

/*  don't wait!  
 *  start processing buffered OpenGL routines 
 */
    glFlush ();
}

void init (void) 
{
/*  select clearing (background) color       */
    glClearColor (0.0, 0.0, 0.0, 0.0);

/*  initialize viewing values  */
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glOrtho(0.0, 1.0, 0.0, 1.0, -1.0, 1.0);
}

/* 
 *  Declare initial window size, position, and display mode
 *  (single buffer and RGBA).  Open window with "hello"
 *  in its title bar.  Call initialization routines.
 *  Register callback function to display graphics.
 *  Enter main loop and process events.
 */
int main(int argc, char** argv)
{
    glutInit(&argc, argv);
    glutInitDisplayMode (GLUT_SINGLE | GLUT_RGB);
    glutInitWindowSize (250, 250); 
    glutInitWindowPosition (100, 100);
    glutCreateWindow ("hello");
    init ();
    glutDisplayFunc(display); 
    glutMainLoop();
    return 0;   /* ISO C requires main to return int. */
}

```

I've also noticed that the files /usr/include/GL/gl.h and /usr/include/GL/glut.h is not there anymore and I therefore suspect that I haven't installet GLUT properly :confused:

Best Regards.

---

### Post by svenskmand on 2008-08-10
All i need is which packes to install.

Best Regards

---

### Post by carlosbertholdi on 2008-08-28
Same thing here, I think i just find out which package to install. Let me test here.

---

### Post by carlosbertholdi on 2008-08-28
I install the freeglut3-dev package and now I have the file glut.h in /usr/include/GL, but i still couldn't compile my example here, but yours example works with a -lglut option.

---

### Post by svenskmand on 2008-08-28
I got it working with


```

sudo apt-get install freeglut3 freeglut3-dbg freeglut3-dev libglu1-mesa libglu1-mesa-dev libglui2c2 libglui-dev libglut3 libglut3-dev

```

hope it works for you also :)

---

