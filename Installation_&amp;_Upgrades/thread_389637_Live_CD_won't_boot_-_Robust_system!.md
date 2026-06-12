---
title: "Live CD won't boot - Robust system!"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Rashind on 2007-03-20
Hello everyone,

I'm getting very frustrated with my system's refusal to boot a live CD.  I've burned 2 normally from the zip package from the main ubuntu site, one using that same filepack along with Nero's boot-cd burning option(though I suspect that makes a DOS-booting CD...), and one from an i386 6.10 ISO from the UColumbia Ubuntu mirror.  None of these will boot in my system, they aren't even recognized as bootable discs.  Each CD, I verified and it checked out... but none of them will boot.

Here are my specs: eVGA 680i (yes, BIOS is up to date), 8800 GTX (seriously doubt this is the problem, since a video card shouldn't be keeping a CD from booting, but what the hey...), Intel C2D E6600, and my optical drives are LG super-multi DVD+/-RW drives.

What gives?  Is there a floppy image floating around from which I could boot and get the live CD going from there?  Is there an alternative disc-image I could burn and maybe get it working?  Would I have better luck with the 64 bit version?  Has anyone else ever had this problem?  I've been searching the forums, and it looks like no one else is getting stuck this early in the game.

---

### Post by Hishgraphics on 2007-03-21
When you said you burned normally, do you mean you created a data CD or burned the ISO as an image file? I'm not too clear about it from your post.

---

### Post by Rashind on 2007-03-21
When I was burning from an ISO, I burned as an image.  When I was burning a data directory (as you get with the main ubuntu download link from the main site), I burned as data.

---

### Post by chewearn on 2007-03-21
When you said the system will not boot, what error message are you getting?

---

### Post by Hishgraphics on 2007-03-21
> Is there an alternative disc-image I could burn and maybe get it working?

Have you tried the alternate iso image? The filename should be: [COLOR="Teal"]**ubuntu-6.10-alternate-i386.iso**[/COLOR]

---

### Post by Rashind on 2007-03-21
Hishgraphics: I haven't come across that.  I'll dig around in the ubuntu mirrors and see if I can find a copy.

AstalaVista: I hit escape to bring up the boot menu (my BIOS allows me to select my boot-source from a menu), then I go to CD-ROM and it tells me that it could not detect a bootable CD.  Then it just boots from the hard drive like a normal boot.

It's unlikely that it's a problem with the drives, since I've tried both of my drives... however, they're the same model drive, so it's possible it's just a problem with all of these LG drives.

---

### Post by Rashind on 2007-03-21
> **Hishgraphics said:**
> Have you tried the alternate iso image? The filename should be: [COLOR="Teal"]**ubuntu-6.10-alternate-i386.iso**[/COLOR]

Okay, I downloaded that file from purdue, burned a CD from the ISO, and my system still is not recognizing it as a bootable CD.  I am just completely at a loss, here.  It'll recognize my XP install disc just fine.  :confused:

Edit: Grammar/meaning cleanup.

---

### Post by ssican on 2007-03-21
It is necessary: 1) Burn the iso image on speed - 4x - ( 600kb/s ). 2) To verify the MD5SUM: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  and see: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)    Installation/CDIntegrityCheck.

---

### Post by Rashind on 2007-03-21
> **ssican said:**
> It is necessary: 1) Burn the iso image on speed - 4x - ( 600kb/s ). 2) To verify the MD5SUM: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  and see: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)    Installation/CDIntegrityCheck.

Thank you.  The installation guide had instructions for making a boot floppy, which worked beautifully.

---

