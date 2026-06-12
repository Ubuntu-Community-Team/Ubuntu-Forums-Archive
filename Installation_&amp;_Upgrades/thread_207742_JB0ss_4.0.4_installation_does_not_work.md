---
title: "JB0ss 4.0.4 installation does not work??"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by AlliumPorrum on 2006-07-02
Hi!

Has anyone managed to install JBoss 4.0.4 to the ubuntu machine?? I ran the installer from console like this:

 java -jar jboss-4.0.4.GA-Patch1-installer.jar

But I always just get the following error:
----------------------------------------------------
PackageListener, install.log=/home/jasurakk/Desktop/Download/install.log
- Error -
java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
java.awt.HeadlessException:
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
        at java.awt.Window.<init>(Window.java:317)
        at java.awt.Frame.<init>(Frame.java:419)
----------------------------------------------------

Does anyone have an idea what's wrong?? What X11 DISPLAY- variable is it talking about?? Where should it be, and in what form??

Or, does anyone know a better way for installing JBoss?

---

### Post by sgtBiafra on 2006-07-06
If you're just running it for development/experimentation purposes, just grab the archived version (tar.gz or tar.bz2). Once you've extracted to a folder, you can execute it from there.

I would think the only fancy thing that the installer would do might be to setup  JBoss as a daemon so that it auto-starts with the system.

---

### Post by Jonathan.Martin on 2006-08-10
I know this is very late after your initial post, but I had no problem runnging the 4.0.4-GA installer. Previously I had taken unzipped the file structure as per previous post, but had problems deploying some of my application. On running the deployer, my app worked OK. Im not sure what the difference between the two installation methods were though.

Cheers,

Jonathan.

---

