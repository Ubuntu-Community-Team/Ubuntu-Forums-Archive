---
title: "How to update Intel Graphics driver"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by mucklas on 2012-07-01
I *need* to update my driver, even though everything seems to work just fine. I got Diablo 3 for my birthday (yay!) and managed to install it using PlayOnLinux. BUT the game won't run, tells me my graphics driver is out of date.
According to the little plastic sticker on my laptop I've an Intel Core i5-480M processor and the grapics card is just presented as Intel Hd Graphics. I don't know if that helps any. I run 11.10.

I kept the pre-installed windows, just repartitioned it when I installed ubuntu, and on my windows boot I was able to install and run the game after updating the driver. I would prefer to run it in ubuntu, though.

---

### Post by Shadius on 2012-07-01
Okay, let's get started! You should be able to simply go to System Settings, then Additional Drivers. Should be a proprietary driver in there that you can use.

---

### Post by mucklas on 2012-07-01
"No proprietary drivers are in use on this system."
There's nothing there. :(

---

### Post by Shadius on 2012-07-01
Okay, let's see what graphics card you have with:
```
lspci -nnk | grep VGA
```

Post the output here.

---

### Post by mucklas on 2012-07-01
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)

---

### Post by Shadius on 2012-07-01
Now I believe you can get the driver from Intel's website. Run the following:

```

lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
```

Then:
```
lsb_release -a
```

Post the entire output within [CODE] tags by pressing the "#" button in the message box.

---

### Post by mucklas on 2012-07-01
I was wondering how to do those handsome output frames...

*lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'*
```
Kernel driver in use: i915
Kernel modules: i915
```

*lsb_release -a*
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

---

### Post by Shadius on 2012-07-01
Hmm...having a hard time tracking down the drivers you need from Intel. :( Could you go into System Settings, Details and check what it says for the Graphics section?

---

### Post by mucklas on 2012-07-01
I went to System Settings, System Info, Graphics; is that what you wanted?
Anyway, It says: Driver: Intel® Ironlake Mobile x86/MMX/SSE2 Experience: Standard

ETA: I'm really grateful for the time and effort :)

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> I went to System Settings, System Info, Graphics; is that what you wanted?
Anyway, It says: Driver: Intel® Ironlake Mobile x86/MMX/SSE2 Experience: Standard

ETA: I'm relly grateful for the time and effort :)

Yupp, you got it! Odd, I'm not finding anything about Intel Ironlake Mobile from the Intel website. :(

---

### Post by mucklas on 2012-07-01
Is there any point in upgrading to Precise Pangolin? Would that solve my problem, or would I still have the same issue?

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> Is there any point in upgrading to Precise Pangolin? Would that solve my problem, or would I still have the same issue?

You might have the same issue. You could test it out first by using a LiveCD. I'm trying to think why there aren't any proprietary drivers listed for you. After all, your graphics card is an integrated card, right?

---

### Post by mucklas on 2012-07-01
Integrated, yes, at least that's what it says on the label. I'm not very good at this... :)

Is this a repository issue? Why the driver isn't listed I mean? Should I enable something?

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> Integrated, yes, at least that's what it says on the label. I'm not very good at this... :)

Is this a repository issue? Why the driver isn't listed I mean? Should I enable something?

That's okay. I didn't know much about Ubuntu when I first started using it either. I still consider myself a beginner. I also wanted to learn how to check what my graphics card was and its driver because I had an issue where Ubuntu was displaying it as "Unknown Driver" in the System Settings. It has magically fixed itself now. 

I don't think it's a repository issue unless something was changed. You could post a screenshot of your Software Sources. Probably the first three tabs, Ubuntu Sofware, Other Software and Updates.

---

### Post by mucklas on 2012-07-01
I don't know how to post a screenshot :redface:
I'll type the first four:

1: **[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric** contrib
2: **Canonical Partners**
Sotfware packaged by Canonical for their partners
3: **Independent**
Provided by third-party softare developers
4: **Independent** (Source Code)
Provided by third-party softare developers

I found [this]("http://www.ubuntuupdates.org/package/xorg-edgers/precise/main/base/xserver-xorg-video-intel") while looking. Could it help?
ETA: Also [this]("https://launchpad.net/~glasen/+archive/intel-driver").

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> I don't know how to post a screenshot :redface:
I'll type the first four:

1: **[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) oneiric** contrib
2: **Canonical Partners**
Sotfware packaged by Canonical for their partners
3: **Independent**
Provided by third-party softare developers
4: **Independent** (Source Code)
Provided by third-party softare developers

I found [this]("http://www.ubuntuupdates.org/package/xorg-edgers/precise/main/base/xserver-xorg-video-intel") while looking. Could it help?
ETA: Also [this]("https://launchpad.net/~glasen/+archive/intel-driver").

To do a screenshot,just press the *Print Screen* key on your keyboard. The screenshot will either go into your Home or Pictures folder. Find it there and attach it here. 

I would try the PPA, the second link you posted. I've tried the X org edgers and it messed up my Ubuntu and I had to go through some troubleshooting to get it back to how it was. I would leave that as a last resort. Let me know if you're going to try it and I will provide the link to my thread that has the fix if anything goes wrong.

---

### Post by mucklas on 2012-07-01
Heh, I can do a screenshot, I just don't know how to post it - "Please enter the URL of your image:" is what the prompt says... But the image is on my desktop...?

Anyway, doing what the second link suggested, [here]("https://launchpad.net/~glasen/+archive/intel-driver"), seems to do it, the game starts at least. The graphics aren't very nice, too dark. Maybe it's adjustable. I also haven't played yet. I'll be back with an update once I have :)

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> Heh, I can do a screenshot, I just don't know how to post it - "Please enter the URL of your image:" is what the prompt says... But the image is on my desktop...?

Anyway, doing what the second link suggested, [here]("https://launchpad.net/~glasen/+archive/intel-driver"), seems to do it, the game starts at least. The graphics aren't very nice, too dark. Maybe it's adjustable. I also haven't played yet. I'll be back with an update once I have :)

Once you've clicked the button for attachments, click the button that says "Choose File" or "Browse", then find your screenshot, and then click "Open", then click "Upload" then close the attachments window. Your screenshot will be uploaded in your post. It seems you're on your way to fixing the issue. Good job!

---

### Post by mucklas on 2012-07-01
Oh, dear. Even with the gamma setting at the highest possible it's still too dark and the game is unbelievably sluggish. Maybe my little laptop can't handle running Diablo in wine :???:

Thank you for helping, I consider it a qualified success; the game starts without problems, and at least i didn't break anything trying to fix the issue :D

Also, thanks for technical help with the forum!

---

### Post by Shadius on 2012-07-01
> **mucklas said:**
> Oh, dear. Even with the gamma setting at the highest possible it's still too dark and the game is unbelievably sluggish. Maybe my little laptop can't handle running Diablo in wine :???:

Thank you for helping, I consider it a qualified success; the game starts without problems, and at least i didn't break anything trying to fix the issue :D
Diablo is a very heavy game and Wine does tend to run programs slowly so there may be some issues there. Try messing around with the settings to get it right, if it's possible. I'm glad that nothing broke too!

---

### Post by nullus on 2012-11-10
I'm having similar sluggish issues, as well as numerous other problems that I think all arise from not having correct drivers for intel HD graphics. (mine is currently ironlake too)

I'm going to try to figure out the correct setup, will repost if I get it working.

---

### Post by deadflowr on 2012-11-10
> **nullus said:**
> I'm having similar sluggish issues, as well as numerous other problems that I think all arise from not having correct drivers for intel HD graphics. (mine is currently ironlake too)

I'm going to try to figure out the correct setup, will repost if I get it working.

Intel graphics drivers are open source only.

You can try to install xorg-edgers to see if a newer version would work better. But that's about all you can do, aside from some super serious code tweaking.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

---

### Post by nullus on 2012-11-17
So does that mean that installing the packages at [http://intellinuxgraphics.org/2012.07.html]("http://http://intellinuxgraphics.org/2012.07.html") won't be able to improve my setup?
[]("http://http://intellinuxgraphics.org/2012.07.html")

---

### Post by diamondburned on 2013-06-29
Well, Intel now has a GUI version of Intel Drivers Update from a third-party company :)
I'm not sure where is the link but I will trying to find it.
I have a game Minecraft too (Pro yay!) But in Windows, the game keep saying Bad video card driver.
Since I used Ubuntu the game could able to start with 620 MB ram, throught Wine :)
P/S: When my computer update, It keep failed :(

---

