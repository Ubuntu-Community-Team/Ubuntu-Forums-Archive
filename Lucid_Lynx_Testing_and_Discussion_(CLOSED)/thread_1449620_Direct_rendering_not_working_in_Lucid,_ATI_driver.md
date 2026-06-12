---
title: "Direct rendering not working in Lucid, ATI driver"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by deusdies on 2010-04-08
Howdy,

Ubuntu 10.04 lucid lynx
ATI HD5750
FGLRX 8.721ubuntu7 installed

Direct rendering just turned off somehow. One day I was playing Warcraft III in Wine just fine, the next morning I start getting this error:

```
err:ole:CoCreateInstance apartment not initialised
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  582
  Current serial number in output stream:  582

```

Since I was suspicious of OpenGL, I ran 

```
glxinfo | grep rendering
```
and got the following:
```
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

Now the thing is that Compiz is working just fine and glxgears as well.

However, running any of the games that require OpenGL doesn't work, giving me different variants of errors.

Here's my xorg.conf (though I've heard this is barely used anymore): [http://pastebin.com/Bzquj3vh](http://pastebin.com/Bzquj3vh)

Any help would be appreciated.

**EDIT: Problem solved. Installed libgl1-mesa-swrast**

---

### Post by lidex on 2010-04-08
Check "/usr/lib/fglrx/dri/swrast_dri.so" if it's a symlink it may be broken. "/usr/lib32/fglrx/dri/swrast_dri.so" also. A lot of updates in lucid and some things get broken, but you knew that right? Still in beta. You should be in the lucid testing forum: [http://ubuntuforums.org/forumdisplay.php?f=377]("http://ubuntuforums.org/forumdisplay.php?f=377")

---

### Post by deusdies on 2010-04-08
Thanks, but:

```
bogdan@ares:~$ sudo updatedb
bogdan@ares:~$ locate swrast_dri.so
bogdan@ares:~$ 

```

In other words, it's nowhere to be found.

---

### Post by lidex on 2010-04-08
Re-install your driver.

---

### Post by deusdies on 2010-04-08
Great minds think alike; I was doing that. But, no luck - still locate finds nothing.

---

### Post by deusdies on 2010-04-08
Problem solved; see original post for details.

---

### Post by jymbob on 2010-04-11
Hmm. I managed to get direct rendering working again (adding the modules to xorg.conf seemed to do the trick), but still can't get wine to do anything requiring GLX. Did installing the above package actually give you the files you needed in the right place? I'm still missing them.

Lucid x64, ATI HD 4870.

---

### Post by deusdies on 2010-04-12
It's a pain to get WinE to use the OpenGL libraries on a 64-bit system. Try uninstalling WinE completely, and then installing the new version (which is supposed to support x64 natively). 

If it doesn't work, you need to get 32-bit OpenGL libraries.

What does the terminal say when you try to run an OpenGL application?

---

### Post by scottiw2000 on 2010-04-13
I'm using the same card (HD4870) and am trying to fix the same problem, but I don't find libgl1-mesa-swrast anywhere in synaptic. Where do I download it? 

Thanks.

---

### Post by lidex on 2010-04-13
Have a look at this page:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by scottiw2000 on 2010-04-14
Thanks, but now I'm more confused. I didn't see anything on the page you suggested about getting the libgl1-mesa-swrast driver. I did what was recommended on that page and downloaded the ati driver installer from here [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English) but now the driver (that was basically working before) isn't working at all. I tried disabling it and re-activating with administration>hardware drivers (where I first installed the ati driver -- the one that originally mostly worked), but it's still broken. Aaarg. Now I can't activate any compiz effects, where before it was just that some opengl effects were choppy.

For clarity, here's my process:
1. installed 10.04 beta fresh with the Radeon hd 4870 card
2. activated the proprietary driver with administration>hardware drivers
3. had very choppy response from docky, which had been quite smooth using the mesa driver
4. followed the advice you linked to and used ati's Catalyst installer (ati-driver-installer-10-3-x86.x86_64.run)
5. now the driver is broken. It is activated under administration>hardware drivers, but compiz tells me there's no driver available. The only compositing available to me is Metacity.

And I still don't know how you downloaded and installed libgl1-mesa-swrast, since I can't find any reference to it anywhere.

---

### Post by scottiw2000 on 2010-04-14
If it helps, glxinfo gives me this:

name of display: :1.0
Segmentation fault (core dumped)

locate swrast_dri.so gives me:

/usr/lib/dri/swrast_dri.so
/usr/lib32/dri/swrast_dri.so

but the file isn't in my /usr/lib/fglrx/dri directory. Any help would be great. I'm really out of my depth here!

---

### Post by lidex on 2010-04-14
What is the output of this command:
```
fglrxinfo
```
And this:
```
uname -a
```

---

### Post by scottiw2000 on 2010-04-15
All I get from fglrxinfo is this:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

uname -a gives me:

Linux ian-desktop-home 2.6.32-20-generic #30-Ubuntu SMP Mon Apr 12 15:20:57 UTC 2010 x86_64 GNU/Linux

I ran the ati driver installer again and did aticonfig --initial -f to reset the xorg.conf settings. But no use.

---

### Post by scottiw2000 on 2010-04-15
ok, now I'm just trying to get my system back to a working open-source setup again. I've uninstalled the fglrx driver using synaptic. But now when I run glxinfo I'm still getting a crash:

name of display: :1.0
Segmentation fault (core dumped)

Any suggestions?

---

### Post by scottiw2000 on 2010-04-15
Alright, I've been pecking away at the problem. I've got the fglrx driver installed again and fglrxinfo is working again. It outputs:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series 
OpenGL version string: 3.2.9756 Compatibility Profile Context

when I run glxinfo now I get "direct rendering=Yes" so openGL seems to be working. The problem is that my screen graphics are still really choppy. It seems like anything with compositing is terrible. Am I right, though, that this is a different problem?

---

