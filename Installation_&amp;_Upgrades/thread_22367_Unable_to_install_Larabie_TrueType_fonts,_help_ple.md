---
title: "Unable to install Larabie TrueType fonts, help please"
date: 2005-03-27
forum: Installation &amp; Upgrades
---

### Post by erkki70 on 2005-03-27
Hi,

I've been searching the forums to figure out and solve this problem by myself but I'm not going any further and need help.
I'm trying to install the ttf-larabie-deco, ttf-larabie-straight and ttf-larabie-uncommon packages from the Hoary Multiverse repository but cannot succeed.
The packages are installed as notified in synaptic, and files are in /usr/share/fonts/truetype as well as /usr/lib/X11/fonts/TrueType.
The thing is that it appears that the symlinks are broken for example in /usr/lib/X11/fonts/TrueType/larabie-uncommon/*.ttf is broken.
(actually, I wonder if something could be missing too...)

I've tried to dpk-reconfigure fontconfig, xserver-xorg, defoma... Also tried to update-fonts-alias TrueType and manually edit xorg.conf to add the FontPaths but nothing works.
I'm stuck and need assistance to avoid messing up my box.
Did I do something wrong?

Could anyone help please. I know those fonts aren't open source and there might be a discussion about providing an open source only environment, but the fonts are a great enhancement IMHO for UI customization as well as "must have" for The Gimp, OOo, Scribus, etc...
Before using Ubuntu, I've been running a Debian sid and font installation always went very nicely.
I'm also wondering about the msttcorefonts which installed perfectly using the same method (synaptic).

Thank you in advance for any suggestion to get those fonts working.

---

### Post by erkki70 on 2005-03-28
Ok, still not working :cry:

I've now tried to reinstall the Ubuntu-desktop package (which also installs ttf fonts for many languages) and I still cannot enjoy the Larabie fonts.
Does anyone have an idea about that?
Is it working for anyone else?
I would be really amazed if there's nobody using these fonts...

Any suggestions really welcome, thanks.

Ok more details in case someone knows about this all.
It looks like the packages are very small and probably not including the fonts themselves as .ttf files.
Also, the only thing I have into /usr/share/fonts/truetype/ are "empty" folders eg. 
 ```
root@Zebra-X:/usr/share/fonts/truetype/larabie-straight # ls -la
total 8
drwxr-xr-x   2 root root 4096 2005-03-28 13:49 .
drwxr-xr-x  17 root root 4096 2005-03-28 13:49 ..
-rw-r--r--   1 root root	0 2004-10-07 17:12 fonts.scale

``` 
When I think folder should contain the .ttf files, just like any other folder does in this same location.

Now, if I go to this directory, it looks like something is really missing:
 ```
root@Zebra-X:/usr/X11R6/lib/X11/fonts/TrueType/larabie-deco # ls -la
total 8
drwxr-xr-x  2 root root 4096 2005-03-28 13:49 .
drwxr-xr-x  5 root root 4096 2005-03-28 13:49 ..
lrwxrwxrwx  1 root root   57 2005-03-28 13:49 *.ttf -> ../../../../../../share/fonts/truetype/larabie-deco/*.ttf

```

Well, it looks like those packages are broken or is it me doing something wrong with that?
Whom to should I report this?
Please help required.

---

### Post by erkki70 on 2005-03-28
And again!

So, after checking as far as I could, it definitely looks like to me that the Larabie fonts packages in the Multiverse repository, are somehow broken or at least incomplete.
I've checked the "original" packages from [http://packages.debian.org/unstable/source/ttf-larabie]("http://packages.debian.org/unstable/source/ttf-larabie")
and they're much bigger than the ones on Multiverse.
Now, I'm a noob and not familiar in procedures such as reporting this problem or is it a "bug"?
Would someone tell me how to proceed?
I'm also not able to figure out alone how to install those fonts from tarball porvided on Debian pages, as the script included doesn't work (well, no idea how to change it and make it work...)
Would be great to have some feedback on that....

---

### Post by NemoTheLobster on 2005-04-04
Try this:

apt-get build-dep ttf-larabie-deco
apt-get -b source ttf-larabie-deco
dpkg -i ttf-larabie*.deb

That's basically what I did to get them working.  I think the debs in the repository just need to be rebuilt.  I went to file a bug on it at one point but couldn't because the packages are in multiverse and aren't supported.

---

### Post by erkki70 on 2005-04-05
[QUOTE=NemoTheLobster]Try this:

apt-get build-dep ttf-larabie-deco
apt-get -b source ttf-larabie-deco
dpkg -i ttf-larabie*.deb

That's basically what I did to get them working. I think the debs in the repository just need to be rebuilt. I went to file a bug on it at one point but couldn't because the packages are in multiverse and aren't supported.[/QUOTE]

Hi and thank you very much for your answer!
Unfortunately, after running the 2nd command in root terminal, I have an error at the end (so I'm only posting the error as beginning of install looks fine):
 ```

# Build the package
dpkg -b debian/ttf-larabie-straight ..
dpkg-deb: building package `ttf-larabie-straight' in `../ttf-larabie-straight_20011216-3_all.deb'.
dpkg-deb: control directory has bad permissions 2755 (must be >=0755 and <=0775)make: *** [binary-indep] Error 2
Build command ‘cd ttf-larabie-20011216 && dpkg-buildpackage -b -uc’ failed.
E: Child process failed
root@Zebra-X:/home/erkki70 #

``` 
Do you have any idea on what should I do to get this to work? Do I miss something?
How could I change the permissions as it looks like building fails because of that?
Thanks for your help. ;)

Cheers,
Erkki

---

### Post by NemoTheLobster on 2005-04-06
Sorry, it had been a while since I made my debs.  For some reason there's a sticky bit set in the permissions.  Try these steps instead:

apt-get build-dep ttf-larabie-deco
apt-get source ttf-larabie-deco
chmod -s * -R
apt-get -b source ttf-larabie-deco
dpkg -i ttf-larabie*.deb

That should get it working.  I've never gotten around to pinning it, so I end up reinstalling my debs after an upgrade.

---

### Post by erkki70 on 2005-04-06
[QUOTE=NemoTheLobster]
apt-get build-dep ttf-larabie-deco
apt-get source ttf-larabie-deco
chmod -s * -R
apt-get -b source ttf-larabie-deco
dpkg -i ttf-larabie*.deb
[/QUOTE]

Thank you so much!!!
Wow, it worked so smoothly and I'm really happy to get those fonts working.
Thanks again for providing the right answer to this. :)
As long as the package is not rebuild, this should be a how-to maybe?

Cheers,
Erkki

---

