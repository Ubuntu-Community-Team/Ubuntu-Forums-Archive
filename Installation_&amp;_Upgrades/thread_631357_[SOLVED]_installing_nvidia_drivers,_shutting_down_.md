---
title: "[SOLVED] installing nvidia drivers, shutting down x server"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Mindflux0 on 2007-12-04
As I have basically no idea what I'm doing I'm having some trouble with this.

I downloaded the nvidia drivers and set them to executable.

Now I have to shutdown the gui and don't know how to do this

I tried ctrl-alt-f1 and then "sudo /etc/init.d/kdm stop" it says it can't find that command.  Also it keeps saying "bcm43xx:  Error:  Microcode  'bcm43xx_microcode5.fw' not available or load failed" every 30seconds or so.

---

### Post by PmDematagoda on 2007-12-04
What VGA card do you have?

And did you try installing the drivers using the Restricted Drivers Manager?

---

### Post by Mindflux0 on 2007-12-04
I have an onboard geforce 6150. The instruction at nvidia said I have to shut down the gui to install properly.

---

### Post by sirdilznik on 2007-12-04
The way I install drivers manually if I have to is to log out and log back in but change the session to "Failsafe Terminal".  This will give you a very basic desktop with an open shell.  From the shell you can cd to whatever directory you downloaded the installer to and run the command:
```
sh NVIDIA-<whatever>
```.  On my machine it complains that X is still running so I do
```
rm -f /tmp/.X0-lock
```
Now I know rm -f is one of the "scary" commands listed in the commands NOT to use and with good reason.  It removes a file or files and should only be used if you know what you are doing.  In this case the file being removed (/tmp/.X0-lock) is only a temporary file telling your system that the X server is still running.  Generally removing files from the /tmp directory is fairly safe since it is a temporary directory and those files will be removed at some point anyway (on shutdown if not sooner) though I wouldn't do it just for the h*ll of it.  After removing /tmp/.X0-lock I can successfully run the NVIDIA installer.  It has always worked for me (regardless of distribution).  If there is a less "scary" way or if I'm doing something bad, please let me know. :wink:

Edit:  You will need root permissions to do these things so you will need to use sudo or something.

---

### Post by Mindflux0 on 2007-12-04
yeah...that sounds like something I don't want to do...
Is there some way to do this by actually shutting down the gui?
Also does anyone know what that error means?
And lastly, nvidia says they don't release direct support for laptop cards and to check with the manufacturers, will the regular drivers function properly?

---

### Post by PmDematagoda on 2007-12-05
You can stop the GUI by using:-

```
sudo /etc/init.d/gdm stop
```

After you install the driver, you can restart the GUI using:-
```

sudo /etc/init.d/gdm start
```

---

