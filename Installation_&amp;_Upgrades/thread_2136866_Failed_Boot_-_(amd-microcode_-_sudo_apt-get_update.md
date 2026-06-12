---
title: "Failed Boot - (amd-microcode - sudo apt-get update fail)"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by NamTaey on 2013-04-18
I am completely stumped.

I attempt to boot into Ubuntu 12.10, I type my code to unlock the disk, and then Ubuntu fails to load.  It is just stuck on the Ubuntu Logo.
I did CTRL + Alt + F1 and I saw that it had failed to load amd-ucode/microcode_amd.bin.

I have the following AMD hardware:
[h=1][[SIZE=2]AMD Athlon II X4 640 Propus 3.0GHz Socket AM3 95W Quad-Core Desktop Processor ADX640WFGMBOX[/SIZE]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103871")[/h][h=1][[SIZE=2]HIS H677FN1GD Radeon HD 6770 1GB 128-bit GDDR5 PCI Express 2.1 x16 HDCP Ready CrossFireX Support Video Card with Eyefinity[/SIZE]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161387")[/h]So I googled around and found several "solutions" to this issue.  However, the most reoccurring solution was to go into recovery and then root and type:
[B]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install amd64-microcode
[/B]
But when I type in apt-get update I get this and several others:

[B]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
[/B]
I googled this too but failed to find a solution.


Am I going about this wrong?
Can someone walk me through this?  I am pretty confused.

---

### Post by mörgæs on 2013-04-20
It sounds like the mirror has simply been down when you tried. Does it work now, maybe after switching mirror?

---

