---
title: "Update Manager stalls in new Ubuntu v10.04 LTS OS"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by scruffyeagle on 2011-07-23
I'm an old hand at Windows, but I'm new to Ubuntu - so, I've got a lot of learning to do. I just set up Ubuntu v10.04 LTS on a Toshiba Satellite A205 notebook. Currently using cable broadband access for internet. Installation seemed to go without a hitch. But, I've had problems with the Update Manager right from the start. It seems to hang, failing to complete whatever it's doing - and, not always at the same point. The most frequent point seems to be when it's going into its &quot;checking&quot; phase, looking for updates. That's what's happening at this very instant. I see the main Update Manager box greyed out, with a &quot;Downloading Package Information&quot; box above it. The active box is completely blank inside. No contents at all. It won't close by clicking the red button at top left, and I'm a little leery about trying to close it by menu-click on the label on the bottom bar. (Don't want to disrupt ongoing processes and cause broken whatevers.) Can anyone help with this? TIA!  Adding extra info: I've booted this OS about 4 times so far, on 3 different days. Every other time I booted for the 1st time on a given day, the Update Manager automatically started checking for updates online; albeit, with a minute or two delay before starting to do its stuff. But today, it didn't automatically start.  I'd come to the forums and read info re. firewalls, and decided I needed ufw w/ gufw. So, I used the Ubuntu Software Center. I found ufw marked as already installed. I found gufw, and installed it. I closed the USC window. That was the point at which I activated the Update Manager to check for software updates online - it started and hung almost immediately with that blank Downloading Package Information box. Which is the condition it's still in a half hour later. After 45(+) min. w/ no suggestions apprearing here, I rebooted using Ctl/Alt/Sysreq REISUB. That seemed to work w/o problem. Once desktop was up again, I tried to investigate software sources via System/Software Sources. It opened the dialog box, but within a few seconds the box was grayed out and none of the controls inside it were available. It would minimize, restore, & close - but not function. My guess, is that this is related to my problem w/ the Update Manager. Another 1/2 hr. has passed. I tweaked the desktop theme, font sizes, and colors. Then, I tried to shut down the machine. It wouldn't do a proper shut down. I threw up a warning dialog box telling me &quot;AT SPI Registry not responding&quot;. Since nobody seems to have any suggestions for assisting me here, the only thing I can think of to do is tell the machine to force closure of the program. Then, tomorrow I'll try to reinstall Ubuntu v10.04 LTS from scratch. I don't mean to hurt any feelings here, but given the simple nature of the things I've attempted so far, I'm beginning to think this OS is fundamentally defective! (That's why I changed the title of this post to its current questioning state.)

---

### Post by bapoumba on 2011-07-24
Looking at your notebook model, it appears people have reported it works out of the box with ubuntu.

How did you install ubuntu?

Please try to place some paragraphs in your post, it is had to read :)

---

### Post by scruffyeagle on 2011-07-24
Hi, bapoumba! Thanks for responding to my post. Sorry about the paragraph thing. I did try 2 or 3 times, but every time I went to preview I found the extra carriage returns had been deleted from the post. It won't let me keep quotation marks, either. It keeps replacing them with the HTML code of &quot;. Anyway, eventually, I had to just accept the situation and submit the post despite its formatting shortcomings. I'm working on a different installation & machine at the moment, but the forum system won't let me do those now either. Hmm...  Well, I just checked via preview and the system won't let me retain insertion of extra spaces, so I can't insert a bunch of spaces as a separation method. I've installed Ubuntu from a disk, onto 3 different machines since I got the disk a few days ago. I've worked at setting up 2 of those installations, and ran into similar problems. A few minutes ago, I posted into the &quot;Absolute Beginners&quot; area questioning whether my problems with the Update Manager should be grounds for a bug report. The 2 installations I've pursued comleting are very different settings (notebook vs. tower, and single installation vs. dual), and the locking up happened in 2 different manners (the moment checking begins vs. opening Update Manager settings dialog box). But there's a common detail found during restart, that the AT SPI is not responding.

---

### Post by bapoumba on 2011-07-24
Hello,

if you have been installing from the same disk and have had error, I would recommend downloading the iso again and burning low speed.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

For the post formatting: do you have the text editor at the top of the post when writing ? Might be you disabled the wysiwyg editor in the userCP. Which browser are you using ?

---

### Post by scruffyeagle on 2011-07-25
Thanks for your replies!

I've been using different systems, so my FireFox version has changed from instance to instance. My most recent post before this was using the default FF version in the v10.04 LTS Ubuntu. Right now, I'm using FireFox v3.6.3 on an XP OS. My editing setting (before this post) has been at "Enhanced Interface - Full WYSIWYG Editing". I've changed it to "Standard Editor - Extra formatting controls" for this post.

Let's use "preview" to see how that worked... Aha! Now, it's retaining the extra carriage return.

Before coming to the forum tonight, I'd finished doing exactly what you recommend - downloading a new copy of the ISO for Ubuntu v10.04 LTS. I'd reasoned (like you) that perhaps my CD has a defect, so I set that as my #1 priority tonight. Now that I've finished downloading my new ISO, I think I should verify that it's pristine - but, I haven't found any pages or utilities for doing that, so far. Any suggestions to guide &/or educate me? TIA!

---

### Post by mastablasta on 2011-07-25
use this to check MD5 sum of the downloaded ISO: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
The disk burning software usually has option to verify the written data.
 
also before reinstall you could try to change the server from where Ubutnu is trying to update (repository server). There are plenty mirrors arround the world, so select one close to you (maybe even in same country) and give it another go. it could be that you somehow chose to use some repository server that has issues for you.

---

### Post by scruffyeagle on 2011-07-25
Thanks, mastablasta!

---

