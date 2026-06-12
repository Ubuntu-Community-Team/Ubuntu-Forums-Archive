---
title: "Radeon KMS"
date: 2009-06-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by super.rad on 2009-06-07
Just found this on phoronix, thought it might interest a few people on here
[https://launchpad.net/~xorg-edgers/+archive/radeon-kms]("https://launchpad.net/%7Exorg-edgers/+archive/radeon-kms")

---

### Post by BwackNinja on 2009-06-07
Very tempted to try this, but I think I'd want to make it easy to revert back first just in case :P.

Had fun compiling this stuff from source a couple times, if this works well, I might just try plymouth as well.

---

### Post by super.rad on 2009-06-07
There is a live cd with all of it installed so if you don't want to mess with your install just download that and give it a go

---

### Post by inportb on 2009-06-07
osnap? where's that? last time i tried the bleeding-edge xorg packages i borked my gui.

---

### Post by sim-value on 2009-06-08
what does that do ?

---

### Post by jerrylamos on 2009-06-08
> **sim-value said:**
> what does that do ?

On my Compaq Presario Radeon Xpress 200 modeset = 0 or modeset = 1 don't seem to do anything.

On Intel video graphics does do something, for example Ctrl-Alt-F1 shows a different smaller smooth font compared to the old fashioned tty.

On my i845 "vesa" is still clearly faster.  KMS gets 42 seconds to do GtkPerf, vesa does it in 27 seconds.

?

Jerry

---

### Post by Progressive on 2009-06-08
This definitely didn't work for me. Don't be surprised if it doesn't for you either.

---

### Post by super.rad on 2009-06-08
> **Progressive said:**
> This definitely didn't work for me. Don't be surprised if it doesn't for you either.

What card have you got? It doesn't work (yet) on r6xx/r7xx cards.

---

### Post by zika on 2009-06-08
This is my experience (I wrote this for Phoronix [http://phoronix.com/forums/showpost.php?p=77906&postcount=17](http://phoronix.com/forums/showpost.php?p=77906&postcount=17) ):

I have ASUS AH3650 (a.k.a. ATI Radeon HD 3650 512M). Machine is 64/bit  AMD Phenom X3 4950 (I think).
I am using Jaunty with 2.6.30./rc8 and 2.6.30-8.999 daily kernel and  radeon driver from tormod`s ppa ...
I`ve tried Your Live/CD (it is 32/bit?)(I am writing this while on it)  and (compiz is not woking but I do not care) I would like to try it on  Jaunty. What is the right way to do that. My 2.6.30/rc8 kernel is not  the right one? I should add Your repository, update what is updateable  automatically and then manually install that kernel? What problems  should I expect on that route to ... ?
**update:** I've upgraded to Karmic in the meantime. So I will try to  follow instructions on the ppa site. The only thing that bugs me is:  what happens if I try to use different (read newer) kernel that is not  from that ppa? Will the kernel be updated on Your ppa in the same rhythm  as it is coming on in mainline ... ?
**update-1:** It was worth of all the "trouble" ... [IMG]http://phoronix.com/forums/images/smilies/smile.gif[/IMG] Glxgears almost doubled,  compiz is not working (who cares) but card is, at last, coming near some  of its previous performances in Ubuntu... Thank You for all the work  You are doing for our little community.
**update-2:** For those who might be interested, it works with  2.6.30-8.999 (from mainline, latest daily) but with crippled speed (the  same as it was in Karmic before I applied updates from Your ppa) but it  boots in 5 sconds less with 2.6.30-8.999 than with Your version of  2.6.30-8-generic. I can live with that 5 seconds more ... [IMG]http://phoronix.com/forums/images/smilies/smile.gif[/IMG]

I'm very satisfied with the upgrade I made today. But that is not a suggestion to anybody out there. It is Your data You have to think of ... I risked mine and, it looks, gained ... :)

---

### Post by super.rad on 2009-06-08
Is your card using the r6xx/r7xx chipset? I thought KMS didn't work for them yet?

---

### Post by zika on 2009-06-08
> **super.rad said:**
> Is your card using the r6xx/r7xx chipset? I thought KMS didn't work for them yet?
RV635 if I remember well. I get certain speed gain. Acceleration is not enabled according to Xorg.log ... It is definitely better than before. Beats me ...
In order to re-check my impressions how I could revert that action of mine? I do not see a way to force "original" karmic versions of the upgraded packages ... am I wrong?
**update:** Yes, I was wrong, it is doable. Just be patient and thorough in Synaptic. I'm back to mainstream Karmic ... :)

---

### Post by Progressive on 2009-06-08
> **super.rad said:**
> What card have you got? It doesn't work (yet) on r6xx/r7xx cards.

My card is R5xx... X1800 to be precise. No dice.

---

### Post by cszikszoy on 2009-06-08
I tried this on my desktop which has an HD3200 based card and no luck here either.  It starts to load find then I get dropped out to the busybox shell.

---

### Post by Progressive on 2009-06-09
Here is my problem...

EDIT: The ISO file seems to be working for me, so I think this problem is either because I set up something wrong or there is a problem with the 64 bit version of KMS.

---

### Post by Progressive on 2009-06-09
OK, I concede.... it is working much better!

---

### Post by BwackNinja on 2009-06-09
Transparency bugs, KMS doesn't modeset to my resolution ( 1360 x 768 ), but modesets to 800x600 instead. DRI2 works though.

---

### Post by Progressive on 2009-06-14
Why might the repo not work for me, but the official xorg-edgers ISO does?

---

### Post by inportb on 2009-06-15
> **Progressive said:**
> Why might the repo not work for me, but the official xorg-edgers ISO does?

Interesting... another reason for me to check out this ISO...

---

### Post by tormod on 2009-06-17
> **Progressive said:**
> Why might the repo not work for me, but the official xorg-edgers ISO does?

Did you install the kms kernel from the repo?

---

### Post by Slug71 on 2009-06-18
I have this Kernel installed but if i upgrade the Kernel will i lose KMS or will it use the KMS Kernel's config file?

---

### Post by Progressive on 2009-06-18
> **tormod said:**
> Did you install the kms kernel from the repo?

yes, I have the kernel installed, as well as the drm and mesa packages that it provides.

---

### Post by BwackNinja on 2009-06-18
*sigh* now getting CS errors that make compiz unbearably slow and unusable. At least metacity works and 3D still works. Will check more later.

---

### Post by tormod on 2009-06-19
> **Slug71 said:**
> I have this Kernel installed but if i upgrade the Kernel will i lose KMS or will it use the KMS Kernel's config file?

Yes, if you install the normal Karmic kernel you will lose KMS. The config file only tells you which options the kernel was compiled with.

---

### Post by tormod on 2009-06-19
> **cszikszoy said:**
> I tried this on my desktop which has an HD3200 based card and no luck here either.  It starts to load find then I get dropped out to the busybox shell.
I guess the same happens with a normal karmic live CD? There is for instance a bug where the live CD does not boot if it detects RAID (dm-) devices, and probably many more.

---

### Post by d-man97 on 2009-08-10
Not sure if this is relevant to those of you having problems (didn't check which card you have), but KMS only works for *500 and lower cards.


Here is some official, distro independent information for radeon:

[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)
[INDENT]See near the bottom for "Building recent version of radeon + mesa + drm".[/INDENT]
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)
[INDENT]Feature listing/progress by chip.[/INDENT]
[http://dri.freedesktop.org/wiki/R300_Portal](http://dri.freedesktop.org/wiki/R300_Portal)
[INDENT]R300 specific portal.[/INDENT]

According to the X team, this stuff has been "mostly" done for a while now (I've been keeping tabs for months). It is quite disappointing that distributions have not put the packages in so they can be tested more and finalized. It's a shame. Kudos to xorg-edgers.

---

### Post by tormod on 2009-08-10
> **d-man97 said:**
> According to the X team, this stuff has been "mostly" done for a while now (I've been keeping tabs for months). It is quite disappointing that distributions have not put the packages in so they can be tested more and finalized. It's a shame. Kudos to xorg-edgers.
If you count Fedora, they have had it for a long time. The reason other distributions are reluctant to jump on radeon KMS is that until now it has meant regressions in terms of performance and stability, and the new functionality is not taken advantage of in larger scale yet. KMS is only "lower" infrastructure and brings new possibilities for the overlaying graphic stack.

Indirect rendering (gears on rotating cube, yay) is the most prominent feature (or bug fix if seen from the user's perspective) that we can enjoy right now. Flicker-free booting will take some more development and changes in the whole boot sequence (Karmic is integrating silent grub and xsplash as we speak). Running X non-root still needs some work in the X server.

If we can get fast user switching with 3D acceleration for all users soon, that would be serious progress in functionality...

---

### Post by jerrylamos on 2009-08-10
> **jerrylamos said:**
> On my Compaq Presario Radeon Xpress 200 modeset = 0 or modeset = 1 don't seem to do anything.

On Intel video graphics does do something, for example Ctrl-Alt-F1 shows a different smaller smooth font compared to the old fashioned tty.

On my i845 "vesa" is still clearly faster.  KMS gets 42 seconds to do GtkPerf, vesa does it in 27 seconds.

?

Jerry

Oops, latest ati radeon update 
    Help Wanted: People with ATI video cards:
does do something!  Sludge!  Video graphics over 100% slower on ati radeon Xpress 200 modeset=1.  See page 7 in the Help Wanted thread....
Maybe? there's some acceleration code pending??  Anyone?

Jerry

---

### Post by tormod on 2009-08-11
> **jerrylamos said:**
> Sludge!  Video graphics over 100% slower on ati radeon Xpress 200 modeset=1.  See page 7 in the Help Wanted thread....
Maybe? there's some acceleration code pending??  Anyone?
How did you measure the speed? DRI2 is still slower than DRI1 on many other cards as well. But it is catching up and I would not be surprised if it is already faster for some operations.

---

### Post by jerrylamos on 2009-08-11
Measured the speed by installing GtkPerf from Synaptic and xserver-xorg-video-radeon from:
deb [http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/kms/ubuntu) karmic main
from Bryce Harrington in Ubuntu-X Digest, Vol 24, issue 1
This is an IBM Thinkpad T40 1.5 gHz P4 with ati radeon mobility 7500.  Results are similar on Compaq Presario 3.33 gHz ati radeon Xpress 200, namely they are both over twice as slow in modeset 1.  I'm out of time, I'll look up the jaunty results.

```
					
________________________		Mode=0 Mode=1 1_slower_by
GtkEntrytime:____________		0.07	0.10	43%	
GtkComboBoxtime:________		2.33	8.87	281%	
GtkComboBoxEntrytime:___		1.56	4.86	212%	
GtkSpinButtontime:_______		0.37	2.96	700%	
GtkProgressBartime:______		0.36	5.12	1322%	
GtkToggleButtontime:_____		0.46	3.05	563%	
GtkCheckButtontime:______		0.26	0.97	273%	
GtkRadioButtontime:______		0.40	1.31	228%	
GtkTextViewAddtexttime:__		1.64	1.75	7%	
GtkTextViewScrolltime:____		0.49	1.60	227%	
GtkDrawingAreaLinestime:__		1.01	2.67	164%	
GtkDrawingAreaCirclestime:		1.31	2.55	95%	
GtkDrawingAreaTexttime:__		8.00	1.89	-76%	
GtkDrawingAreaPixbufstime:		0.77	3.01	291%	
	---				
Total	time:___________________	19.04	40.72	114%	

```					
  
Jerry

---

### Post by jerrylamos on 2009-08-11
Here's jaunty on the same Thinkpad T40.  Is there another PPA with some improvements?
On this video graphics test, karmic A3 modeset on radeon mobility 7500 is three times slower....

GtkPerf0.40Aug1117:35:092009				
karmic.A3.radeon.Mobility7500.1:6.12.99+git20090805.bd03977e-0ubuntu2				
```
				
_______________________		      jaunty A3_mode0 Modeset=1
GtkEntrytime:____________		0.13	0.07	0.10
GtkComboBoxtime:________		1.78	2.33	8.87
GtkComboBoxEntrytime:___		1.08	1.56	4.86
GtkSpinButtontime:_______		0.32	0.37	2.96
GtkProgressBartime:______		0.86	0.36	5.12
GtkToggleButtontime:_____		0.35	0.46	3.05
GtkCheckButtontime:______		0.31	0.26	0.97
GtkRadioButtontime:______		0.60	0.40	1.31
GtkTextViewAddtexttime:__		1.29	1.64	1.75
GtkTextViewScrolltime:____		0.51	0.49	1.60
GtkDrawingAreaLinestime:__		1.74	1.01	2.67
GtkDrawingAreaCirclestime:		1.34	1.31	2.55
GtkDrawingAreaTexttime:__		1.78	8.00	1.89
GtkDrawingAreaPixbufstime:		0.44	0.77	3.01
				
Total___	time:___________	12.54	19.04	40.72

```				

Jerry

---

