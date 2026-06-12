---
title: "Need to downgrade to edgy...PLEASE help...desperate."
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by KuruOujou on 2007-05-09
Well, the title pretty much says it all. After searching on both Google and the Ubuntu Forums, I could not find a way to do it. I don't really care how complex it is, as long as it is possible and I don't need to wipe my system...again.  I probably shouldn't have done a straight upgrade from dapper to feisty...but I had trouble with edgy...now I would take edgy over feisty. So, can anyone help...please? I'm kindof desperate. (the issues I have been having: USB stops after a while *fixed* But, as a direct result, now my system randomly crashes complete with the caps lock key blinking, but I have found no fix that works.)

I don't see any reason why my system specs would be necessary, but if you need them, feel free to ask. I'm using my feisty system now, but who knows how much longer until it crashes...

---

### Post by starcraft.man on 2007-05-09
> **KuruOujou said:**
> Well, the title pretty much says it all. After searching on both Google and the Ubuntu Forums, I could not find a way to do it. I don't really care how complex it is, as long as it is possible and I don't need to wipe my system...again.  I probably shouldn't have done a straight upgrade from dapper to feisty...but I had trouble with edgy...now I would take edgy over feisty. So, can anyone help...please? I'm kindof desperate. (the issues I have been having: USB stops after a while *fixed* But, as a direct result, now my system randomly crashes complete with the caps lock key blinking, but I have found no fix that works.)

I don't see any reason why my system specs would be necessary, but if you need them, feel free to ask. I'm using my feisty system now, but who knows how much longer until it crashes...

Far as I know, upgrading is a one way process... it would get very messy if it went back >.> You need a clean install.

Can I make a recommedation though? Download the live or alternate installer of Feisty and do a clean install of that, your problems may simply stem from trouble upgrading... there have been known issues, like people who used automatix2 installer, people who left 3d drivers on/installed, and other assorted unofficial software has caused trouble in upgrade.

So, go here, download the Feisty installer of your choice and give it a whirl, you won't be disappointed if you can get Feisty to work, if it fails least ya tried and you can just put Edgy back. Download Edgy at the same time I guess, as a copy for future or if you need it.

[Here]("http://releases.ubuntu.com/") is a link for ISOs. Give it a try :)

---

### Post by KuruOujou on 2007-05-10
Thank you for your quick response. I will try that, I really hope you are right. I am downloading Feisty now, but I am not sure if I will be able to get a full download in with my computer randomly crashing...except I just realized I already have a feisty cd, but I suppose it could be that couldn't it. hmm, back to downloading then.

---

### Post by zanoman on 2007-05-11
I also have troubles  with a FRESH install of Feisty and I miss my previous Edgy.
bluetooth had problems (not sure if I fixed 100% yet).
scanner has problems (tested and working on another machine). :(

---

### Post by Tanker Bob on 2007-05-11
The bad news that I discovered last night is that scanner support was broken in the Feisty kernel.  They used a switch to help laptops with USB suspend, but it broke desktop USB scanner support.  There are some cumbersome work-arounds for some scanner models, but nothing for newer ones.  Supposedly the Linux kernel team fixed the issue recently, but the ubuntu team has yet to implement it.  So, if you want trouble-free USB on a desktop or just want your scanner to work, you have to go back to Edgy.  Best bet there is a clean install.

Here's a helpful hint, though.  I'll assume a single hard drive.  Allocate about 10 GB  or so on your HD for the Linux system (the '/' partition), a small portion for swap, then the rest of your HD as the 'home' partition.  All your user data goes in the home partition, so you can clean install OSes to your heart's content in the system partition without endangering your data.  Even your Firefox and Thunderbird profiles will be picked up by a new system install.  Works great for me.

---

### Post by KuruOujou on 2007-05-11
Well, I think I fixed my random crashing issue, so I don't really need to reinstall anymore. However, that seems to be great advice and I will definately use it next time I need to do a reinstall (probably when the next version comes out). Thank you very much for helping me, though.

---

### Post by Tanker Bob on 2007-05-11
You're very welcome.  I'm glad that you solved your issue!

---

