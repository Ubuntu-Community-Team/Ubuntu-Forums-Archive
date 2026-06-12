---
title: "Wacom/Tablet support status?"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by executorvs on 2009-09-09
I am, among my friends, frequently the go to person for computer issues. several of my friends use tablets like the hp pavilion tx2500 series and have made a partial transition to linux.

so my question is, can anyone give me some information I could pass along as to the status of the wacom driver implementation in karmic. 
also, I read that the newer version of xrandr would handle screen rotation better than it does at current.. is this true?

thank you for any info.

---

### Post by MacUntu on 2009-09-09
Well, that bug is pretty nasty: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

Other than that my Wacom Bamboo works fine.

---

### Post by executorvs on 2009-09-09
I was thinking more about the fact that in some cases hal doesn't seem to correctly parse the hardware information for some wacom touchscreens and styluses. It has been annoying attempting to find walk throughs or figuring out how to edit the .dfi file correctly.

---

### Post by zoomy942 on 2009-09-09
my Tablet PC works perfectly in 9.10

---

### Post by executorvs on 2009-09-09
that's what I was hoping. with luck the gdm error which kept the daily-live I burned yesterday from loading on her tablet will be fixed soon.

---

### Post by MacUntu on 2009-09-09
> **executorvs said:**
> I was thinking more about the fact that in some cases hal doesn't seem to correctly parse the hardware information for some wacom touchscreens and styluses. It has been annoying attempting to find walk throughs or figuring out how to edit the .dfi file correctly.

Sorry, I somehow confused graphic tablets with tablet PCs. Didn't know they come with Wacom technology too. :)

---

### Post by executorvs on 2009-09-09
I should have been clearer.

---

### Post by Roswellgrey on 2009-09-10
The tablet functionality that I have tried ( i.e. the simple stuff !) works just fine on my old Tosh R10

---

### Post by Favux on 2009-09-22
Hi everyone,

Loic2 reports they fixed the cursor offset bug MacUntu mentioned upstream and gives links to the patches in post #314 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=32](http://ubuntuforums.org/showthread.php?t=967147&page=32)

It would be good to get the fix into Karmic.

---

### Post by gali98 on 2009-10-04
I have the tx2000z. On karmic, the tablet works great with a small amount of configuration. (You only need to change one file for everything to work.)
Rotating with xrandr works great on Jaunty, but for the present karmic beta, it seems to be broken... See this bug:
[https://bugs.launchpad.net/ubuntu/+source/x11-xserver-utils/+bug/442722](https://bugs.launchpad.net/ubuntu/+source/x11-xserver-utils/+bug/442722)
To get the tablet working use Favux's tutorial:
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
or my tutorial for fdi:
[http://ubuntuforums.org/showpost.php?p=7093065&postcount=104](http://ubuntuforums.org/showpost.php?p=7093065&postcount=104)

Also @favux, I think the bugfix was released judging by the comments on the bug report:
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

And I have not noticed any offset in my playings so far...

Back to the Original Question though, any wacom tablet on the market should "work" except for the newest one, the bamboo touch (and pen.) Support for it should come in the coming months...
Kory

---

### Post by zoomy942 on 2009-10-04
agreed.  due to several amazing members here, tablet PC's work great

---

