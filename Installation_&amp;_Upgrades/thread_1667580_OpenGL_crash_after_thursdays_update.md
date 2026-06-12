---
title: "OpenGL crash after thursdays update"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Lars on 2011-01-15
Hi.

Yesterday, I noticed that Minecraft stopped working (ie. crashed after the login screen, with an error "BadDrawable")

At first I thought it was an internal error in Minecraft, since it ran an update before trying to start.
Now, I tried to check a few things;

- Mincraft crashes, leaving this error message:

--- BEGIN ERROR REPORT a1dce528 --------
Generated 15/01/11 10:19

Minecraft: Minecraft Beta 1.2_01
OS: Linux (i386) version 2.6.35-24-generic-pae
Java: 1.6.0_22, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: X Error - disp: 0xa088c58 serial: 162 error: BadDrawable (invalid Pixmap or Window parameter) request_code: 138 minor_code: 4
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxContextImplementation.nMakeCurrent(Native Method)
	at org.lwjgl.opengl.LinuxContextImplementation.makeCurrent(LinuxContextImplementation.java:117)
	at org.lwjgl.opengl.Context.makeCurrent(Context.java:182)
	at org.lwjgl.opengl.Display.makeCurrent(Display.java:730)
	at org.lwjgl.opengl.Display.makeCurrentAndSetSwapInterval(Display.java:896)
	at org.lwjgl.opengl.Display.create(Display.java:860)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:280)
	at net.minecraft.client.Minecraft.run(SourceFile:643)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT f09b76c8 ----------


- The Nvidia Settings app crashes when I click the "OpenGL/GLX Settings" on the left, leaving this error message in terminal:
****
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 539 error_code 3 request_code 138 minor_code 4)
***


- Regnum online also crashes after the login screen, leaving the same error message as nvidia-settings app, except "serial" is "34".

I have the latest Nvidia driver, 260.19.29, from what I can see on the nvidia website.

To me it sounds like something in update from Thursday could be the suspect.
Attached is a screendump from the software centre, listing my updates from Thursday.

Has anybody experienced the same problem, and do anyone perhaps know where the problem lies and know how to revert back the earlier version of the faulty app/service?

Hope you guys can help, as I'm at a loss here.. I still feel like a Linux noob... :)

Regards,
Lars

---

### Post by Lars on 2011-01-16
To follow up, the problem was solved by reintalling the newest nvidia drivers.
It seems something from the update bogged up the graphics driver - that's my take on it anyway.

A more detailed "how-to":
I downloaded the newest driver from the nvidia website.
Then I uninstalled the existing driver (which was the same version as the one I DL'ed) by running the nvidia-uninstall command from terminal.
Then I rebooted into debug mode, choosing the terminal with network driver from the menu.
I then ran the nvidiaxxxxx.run file (you might have to do a "chmod a+x" on the file first). It then advised me to run "telinit 3" to change the mode I was running in, so I skipped the installation and did as advised.
Then ran it again, and the installation went smoothly.
Upon reboot it seems that all is good again. :)

---

### Post by Lars on 2011-01-16
oops.. multipost caused by proxy error... :/

---

### Post by Lars on 2011-01-16
is there a way to delete messages?

---

