---
title: "How to install ubuntu on external USB HDD"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by jipbuntu on 2011-04-10
Hi
I installed Ubuntu 10.10 on my external USB HDD (320 GB with 2 NTFS, 1 ext4 and 1 swap partition)
I installed the bootloader into my external hard disk
I am able to boot into my ubuntu installation in my laptop by choosing USB boot option at BIOS start up
Though I have access to two modern PCs with USB boot capability, i am  not able to boot into the Ubuntu installation on my external HDD.
After I choose USB boot , I just get a black screen with a blinking cursor at the left. The grub menu option does not load
How do I work around this problem?
Help please
Ive tried with beta version of NAtty as well. Still does not work
Help!

---

### Post by Hedgehog1 on 2011-04-10
Your issue is not a failed install.

Instead, when you installed on the laptop, you loaded video drivers for the laptop's video card.

Those video drivers are not compatible with the video cards on your 2 other PCs.

Here is the rub: I use a very fast USB stick I boot on lots of PCs (a smaller version of what you are doing), and I go through great lengths to never load any video drivers.  I use the default and it works on most every PC.

**HOWEVER **Natty uses Unity - Unity uses Compiz and Compiz needs video drivers for many PCs.

So while you can create a generic 10.10 disk that will work on most all PCs, you will not be able to make a generic Natty/Unity one.

***The Hedge***

:KS

---

### Post by jipbuntu on 2011-04-10
Hi Hedgehog
What I did forgot to mention in my question was that I tried creating an installation on external USB HDD of both 10.10 and 11.04 beta using a live usb on the PC as well.
Still no luck
Even the grub menu did not show up
I wonder whats wrong?

---

### Post by jipbuntu on 2011-04-10
Actually
Im not able to boot into a full installation of any linux distro on my external HDD in my PC. But i am able to boot into the same distro using my laptop.
Whats wrong with my PC
Im able to boot into live USB without any difficulty.
Im able to see the HDD at BIOS boot screen option menu

HELP!HELP!

---

### Post by oldfred on 2011-04-10
Plug the external in and run this. If it is just video drivers, this may not tell anything.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If you are running script from a Natty install download this version:
Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```

---

### Post by amerinde on 2011-04-10
> **Hedgehog1 said:**
> Your issue is not a failed install.

Instead, when you installed on the laptop, you loaded video drivers for the laptop's video card.

Those video drivers are not compatible with the video cards on your 2 other PCs.

Here is the rub: I use a very fast USB stick I boot on lots of PCs (a smaller version of what you are doing), and I go through great lengths to never load any video drivers.  I use the default and it works on most every PC.

**HOWEVER **Natty uses Unity - Unity uses Compiz and Compiz needs video drivers for many PCs.

So while you can create a generic 10.10 disk that will work on most all PCs, you will not be able to make a generic Natty/Unity one.

***The Hedge***

:KS

are u using an installation or just the live cd. i think since he did an install here... video could have a problem, but more with grub giving an uuid number for the laptop, and now, on another pc, the drive gets a new id and grub cant find it... but for me, i atleast got an error from grub.

---

### Post by jipbuntu on 2011-04-12
Hi 
Success!
I realized there was something wrong with the partitoning in my USB HDD
I re partitoned it and put my ext4 partiton 1st followed by my NTFS partiton containg data.
Further I made sure I unmounted my drive during install
Now Natty boots like a charm
The next test is whether everything works smoothly even after a distruo update
Thanks for the support

---

