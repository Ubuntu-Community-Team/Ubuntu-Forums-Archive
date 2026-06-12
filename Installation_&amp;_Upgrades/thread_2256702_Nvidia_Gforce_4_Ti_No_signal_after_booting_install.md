---
title: "Nvidia Gforce 4 Ti: No signal after booting installed Lubuntu 14.10"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by m4x2 on 2014-12-14
Hey,

UPDATE:
Meanwhile i managed to install Lubuntu on my HDD using the Alternate ISO.
Checksums are correct.
**The problem still exists**.

PREV POST:
i've built an old pc in a beer crate.
I created a boot disk to install Lubuntu 14.10.
The screen with language select showed up, also the screen where i'm able to select "Try Lubuntu without installing" and "Install Lubuntu".
After choosing one of them (both giving me the same result), and after the line at the top left corner flashes, I'm getting a black screen and my monitor behaves as there would be no signal. (Signal light blinks)

This is my system:
Mainboard: MSI KT3 Ultra
Graphics card: Nvidia Gforce 4 Ti
RAM: G.Skill 512Mb DDR PC3200
HDD: Maxtor Diamondmax 10 200gb

I'm going to update you about the processor and BIOS.

regards

p.s. for your information: my montor is a samsung syncmaster 32'

---

### Post by Rex Bouwense on 2014-12-14
Perhaps you got a bad download.  Did you check the MD5Sum on your download?  The hashes have to match.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by m4x2 on 2014-12-14
Thanks for your answer.
Meanwhile i managed to install Lubuntu on my HDD using the Alternate ISO.

**The problem still exists**: After rebooting my system, i'm getting the same issue. 
"[COLOR=#000000]I'm getting a black screen and my monitor behaves as there would be no signal. (Signal light blinks)"

I also checked MD5 checksums of both, Lubuntu desktop ISO and Lubuntu alternative ISO.
Both checksums are correct.

regards

[/COLOR]

---

### Post by mörgæs on 2014-12-15
Checksums are almost always correct. I hardly ever see a thread where a bad download is the explanation.

Have you tried the **nomodeset** boot option?

---

### Post by m4x2 on 2014-12-15
Thanks for your answer.
I already tried a live boot session with the nomodeset option.
The result was the same.
Should I also try to reinstall lubuntu with the nomodeset boot option checked?

regards

---

### Post by mörgæs on 2014-12-15
If you reinstall I suggest something 12.04 based as for example Bodhi Linux, not as a general rule but because you have a certain type of old Nvidia graphics card. 

Please see the link in my signature for more info.

---

### Post by m4x2 on 2014-12-17
I wanted to try out Bodhi Linux, but I got stuck after I chose: "Bodhi Linux live boot"
After I chose that, my montior again behaves as there would be no signal (also blinking signal lights).

regards

---

### Post by mörgæs on 2014-12-17
All advice I can think of is in the link I mentioned before. Doesn't any of it work?

---

### Post by m4x2 on 2014-12-17
If you are refering to the [old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") thread:

1) 
I wasn't able to run lubuntu 14.10 nor Bodhi Linux in live boot.
Most I achieved was to run the installation interface of lubuntu 14.10's alternative iso.
I could also try to install lubuntu 14.04, but I can't find the alternative iso. (desktop iso installation interface is too heavy)

3)
I already figured out that i am not able to use the standard lubuntu ISO. I have to use the alternate ISO.

2), 4) - 9)
I can't run the terminal if i am not able to run a distro, can I?

If you are refering to your [I upgraded, and now I have this error...]("http://ubuntuforums.org/showthread.php?t=1946145") thread:

1)
I already tried boot options like "nomodeset"

2)
Other versions of buntu didn't work aswell so far.
 
3)
I already ran the memory test. No issues were indicated.
I doubt that the problem has something to do with the hard drive, because Lubuntu 14.10 installation (alternate iso) was sucessful and so the read/write access should also be fine.

5-8 is assuming that live boot works, but it doesnt.

regards

---

### Post by mörgæs on 2014-12-17
I was thinking of VESA graphics as mentioned in Old Hardware.

---

### Post by m4x2 on 2014-12-20
Sorry for this "late" answer,

i tried to live boot lubuntu with different vga settings, also with the nomodeset option checked.
Same problem as before occured. 
I'm trying to reinstall lubuntu with the vga=791 option right now.
I really become desperate right now :s

**UPDATE**
Oh my gaaaaaawd, guys I finally got it running!
After i installed lubuntu 14.10 once again with nomodeset option checked and the vga=791 option enabled, I FINALLY GOT IT RUNNING! I'm the happiest human on earth! :D
Thanks for your help! ^^

regards

---

### Post by mörgæs on 2014-12-20
Congratulations. Persistence is a virtue :-)

---

