---
title: "jre for Songbird"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2008-07-11
I updated my Songbird just now, and then tried to us a add on which requires a proper  version of jre, and I downloaded the correct file

(jre-6u7-linux-i586.bin) but I am not sure where it is to be placed, and how to open the file in the first place 

is there a how to on  how to do this?

thank you:confused:

---

### Post by Pumalite on 2008-07-11
Why dont you try Synaptic. In a binary file, you can right click and make it executable in 'Permissions'. It install by itself by a double click afterwards.

---

### Post by kystorms on 2008-07-11
> **Pumalite said:**
> Why dont you try Synaptic. In a binary file, you can right click and make it executable in 'Permissions'. It install by itself by a double click afterwards.

well, i tried to give it permission ( from right click) but then afterwards, when i double click it, i get an error that there is NO program to open it with?

and I tried to find 6u7 in synaptic, but only has 6, and to run the media function in Songbird, need to have this update

thank you
:-)

---

### Post by Pumalite on 2008-07-11
sudo apt-get install build-essential
(if you don't have it yet)

---

### Post by kystorms on 2008-07-11
okay, followed that, and still nothing.... same error code

is there a step after installing build essential?

sorry, new to this

---

### Post by Pumalite on 2008-07-11
There must be instructions on the site where you downloaded from.

---

### Post by kystorms on 2008-07-11
yes, there was... and i followed them, but I know I am doing something wrong, because it does not work.

I guess I just need to know how to place the file where it sh ould be, and then how to run it.

but thank you for your help.

:-)

---

### Post by jamesstansell on 2008-07-11
Java 6 u7 was just released in the last day or two.  I believe it's been packaged for intrepid, but probably not yet for hardy or earlier.  It may be possible to use the intrepid package on hardy but probably more effort than it's worth.

Just curious, do you know why u7 is required?  Since it fixes security problems I have no doubt that it will be back-ported, but I'm still surprised to hear that anything insists on having it already.

To use the .bin file from Sun you need to follow their instructions at [http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting](http://java.sun.com/javase/6/webnotes/install/jre/install-linux.html#self-extracting) (I assume you're 32bit and not 64bit.)

To follow the instructions you'll need to use the command prompt.  Don't try to do it with a graphical file manager.  Also, be sure to install to a brand-new directory.

To get the plugin working there are additional instructions at [http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#plugin](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#plugin) and [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html) but you may have to play a little to get the symbolic link to the right directory.

I'm not sure about Songbird, but Firefox will sometimes load multiple java plugins (as seen in about:plugins) but doesn't let you control which it will use.  So of course it usually uses one that you don't want used.  Just one more thing to watch out for.

---

### Post by kystorms on 2008-07-12
In Songbird, I am trying to use the Album Applet, which wont load ( however , mediaflow does for some weird reason) when I check the page for the applet, suggest must have java running. I then proceed to the suggested page at sun where it tells me I do not have java running on my machine ( which I know I do have 6 running on here, loaded it in Synaptic) but the test at Java fails for my machine.
Yes, I do have a 32 bit machine.

If I could get this applet to run with 6 I would be grateful, is there perhaps a way to test if I do have the correct java some where else besides the Java site?

thank you for your help
I did follow the steps via terminal and it consistently fails, just keeps telling me I do not have the right folder, when I have cd's right to it.

:confused:

---

### Post by jamesstansell on 2008-07-13
I'm not sure if this will work for Songbird, but this page shows your plugins for Firefox and other browsers:

[http://gemal.dk/browserspy/plugins.html](http://gemal.dk/browserspy/plugins.html)

After the plugin list there is a link for more detailed information.  The following page actually loads a java applet to determine version information.

[http://gemal.dk/browserspy/java.html](http://gemal.dk/browserspy/java.html)

---

### Post by kystorms on 2008-07-13
many thanks for that!!! I will be keeping that page in my list of how to's

:-)

---

### Post by Pumalite on 2008-07-13
You can thank him properly by clicking the star in the lower right.

---

