---
title: "Installed JDK 1.5_06, and always get HeadlessException"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by AndriusBurokas on 2006-07-31
How do I configure X or whatever it is called, so that the java could be used to create GUI. Whenever I try to launch some swing or awt program, I always get java.awt.HeadlessException in return.

I'm pretty new to Linux and all what is concerned with it, but the installation went good.

As I can understand, java can't find the monitor for displaying graphips, I would appreciate if somebody could help me.

Steps I followed:

Installed Dapper,
used Synaptic Package Manager to install JDK:
  sun-java5-bin
  sun-java5-demo
  sun-java5-doc
  sun-java5-fonts
  sun-java5-jdk
  sun-java5-jre
  sun-java5-plugin
  sun-java5-source
removed
  gij-4.1 and some other dependant package, because these didn't let me use the Sun java.

and that's it, when I compile and run the program as simple as this one:

import javax.swing.*;
public class Z extends JFrame {
    public static void main(String args[]) {
        Z z = new Z();
        z.add(new JLabel("Hello World"));
        z.pack();
        z.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        z.setVisible(true);
    }
}

I always get the exception:

Exception in thread "main" java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
        at java.awt.Window.<init>(Window.java:317)
        at java.awt.Frame.<init>(Frame.java:419)
        at java.awt.Frame.<init>(Frame.java:384)
        at javax.swing.JFrame.<init>(JFrame.java:150)
        at Z.<init>(Z.java:3)
        at Z.main(Z.java:5)

can You explain me what is a X11 DISPLAY variable, and how do I set it?

Thanks again.

---

### Post by dschulz on 2006-07-31
are you trying that in a tty?? 

if so, please use a terminal emulator in a graphical session. It should work.

Also, you can try by setting the DISPLAY variable like this,


 $ DISPLAY="localhost:0.0" java MySwingProgram


or 

 $ export DISPLAY="localhost:0.0"
 $ echo $DISPLAY
 localhost:0.0
 $ java MySwingProgram

---

### Post by AndriusBurokas on 2006-07-31
I just did an export an got another kind of exception:

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using 'localhost:0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$000(X11GraphicsEnvironment.java:53)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:142)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at java.awt.Window.init(Window.java:270)
        at java.awt.Window.<init>(Window.java:318)
        at java.awt.Frame.<init>(Frame.java:419)
        at java.awt.Frame.<init>(Frame.java:384)
        at javax.swing.JFrame.<init>(JFrame.java:150)
        at Z.<init>(Z.java:3)
        at Z.main(Z.java:5)

I'm working on a local computer, and trying to run java using Konsole

---

