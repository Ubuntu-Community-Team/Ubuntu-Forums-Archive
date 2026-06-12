---
title: "flash in 10.04 beta 1 64bit"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2010-03-27
downloaded  libflashplayer.tar.gz   extracted it, but when i try to copy the extracted libflashplayer.so  into the usr/lib/mozilla/plugins folder, i get the following error:

Error opening file '/usr/lib/mozilla/plugins/libflashplayer.so': Permission denied

why is it saying it can't open it, when i'm just trying to "copy" it into the folder? I'm a little confused. 
Thanks in advance for any help.
Smitty

---

### Post by QIII on 2010-03-27
How are you trying to move it?  In Nautilus (the graphical interface) or from the CLI?

---

### Post by bigsmitty64 on 2010-03-27
I open the folder, right click the tar.gz file, then choose extract. Then I tried copy/paste, AND drag the extracted file into the other folder.

---

### Post by QIII on 2010-03-27
You won't be able to do it that way.  You need elevated permissions to move that file to the intended destination.

First, is the file currently in your Home partition (/home/whoeveryouare)?  If so, it's easy.  If not, put a copy there.

You will need to use the Command Line Interface (CLI) with elevated privileges.

Click Applications | Accessories | Terminal

Type the following at the prompt:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```You will be prompted for your password.  Type in your login password.  You won't see anything happening on the screen.  That is normal.

The file will be copied (what I just told you to do was copy (cp) not move (mv)) to the directory where you need it.

Your prompt will come back in a flash.

If you want to see that it has been copied, use Nautilus again to check to see if it is there.

(Note:  in the CLI, "sudo" temporarily raises your privileges to pretty close to root.  The elevated privilege lasts about 15 minutes, so that you are not indefinitely subject to security issues.)

---

### Post by QIII on 2010-03-27
On second thought, you could 

```
gksudo nautilus
``` and use the graphical interface, but if you're in the CLI already, might as well do what I said above.

---

### Post by bigsmitty64 on 2010-03-27
I did it in cli, and it shows up in the proper folder now, but I still have no flash. As in youtube videos and such.

---

### Post by bigsmitty64 on 2010-03-28
I got it to work, 
Synaptic Package manager, type :

Flashplugin-installer or nonfree (forget which one I used), mark for installation ,apply, restart firefox

Thank you for your help, I really appreciate it.

---

### Post by QIII on 2010-03-28
That has given you the 32-bit version with nspluginwrapper.

Just as well for most people.  64 bit Flash for Linux is a long-standing Beta and is not perfect.

I use the 64 bit version, but know all the ins and outs of making it work well.

---

### Post by bigsmitty64 on 2010-03-29
> **QIII said:**
> 
I use the 64 bit version, but know all the ins and outs of making it work well.

What am I doing wrong with it? I did it (I'm pretty sure) the way you said the first time.

I find that, with this way I did it, it works (can watch a vid on youtube) but I cannot adjust volume or use the slider, or the pause/play in the vid.

---

