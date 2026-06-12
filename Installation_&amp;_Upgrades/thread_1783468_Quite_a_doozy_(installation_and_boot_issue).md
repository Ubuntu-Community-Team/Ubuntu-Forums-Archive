---
title: "Quite a doozy (installation and boot issue)"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by SchwinnSj on 2011-06-15
So. I am currently running ubuntu quite smoothly on my 2002 aftermarket modified dinosaur. And have a 2008 (ish) intel macbook on mac os snowleapord 10.5 (ish) owned by my school. I am also in possesion of a 500 gb seagate goflex usb 3.0 compatable hdd. My aspirations are to install (x)ubuntu onto my external hard drive and use it to boot to both my mac and my ubuntu booted pc. At home there is also a windows seven computer that belongs to my family. So in order to get the mac booting to the xubuntu live cd (which i actually have installed to a small flash drive) (because macs don't like booting to linux) i am using a bootloader called PloP installed to a cd I have a 10.4 xubuntu live cd (usb) which runs like a charm through PloP. However, every time I install xubuntu onto the hard drive it completes with no errors but then refuses to boot past grub where it gives me either a " yes. Just a quote. And is immediatly followed by the light on my hdd going out (no my device is not being physicly disconnected). OR a "hd0 is out of disk". I question whether or not this is a grub error? If there is any other information needed i would happily comply. But the mac cant boot to a cd normally because it doesnt like linux. My old pc cant boot from cd because its too old (it only has a floppy boot option :0) and only the new pc is capable of burning iso's. I also refuse to install directly these three devices because i cant write to my home computer or mac (hence the external hard drive) any help would be much appreciated.

I am a nooby. But i like to think my self clever and capable enough to hopefully follow any guidlines or steps you give me. So long as they are clear
Thanks, Sean

---

### Post by Quackers on 2011-06-15
Welcome to UF :-)
Macs use some kind of EFI arrangement which makes things considerably more difficult (for grub at least).
You may be better off asking in the Apple Users section of the forums.

---

### Post by oldfred on 2011-06-16
You have two issues. As Quackers suggests the Apple forum may be able to help more with your Mac.

Since your new drive is 300GB and your old computer is from 2002 have you run into the old 137GB boot limit. Out of disk would be an error that that might give.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

Did you create a /boot partition or keep all of / (root) inside the first 137GB and make the rest of the drive /home?

---

### Post by SchwinnSj on 2011-06-18
right Quackers, I'll make sure I post it on the mac forum, Thanks. and currently I am just using one massive 150 GB partition mounted on /. I was doing this because (first of all it was a 500 GB hard drive but...) i want 150 Xubuntu and 150 mac OSX with the rest unformatted for later use once i get more ambitious. I'll definitly get my linux partition under that limit though. but how would you recommend i set up the mounting?

---

### Post by Quackers on 2011-06-18
There's nothing wrong with one large root partition. The other option is to have a small root partition (say 12GB) and the rest as a separate /home partition. This can be advantageous if you need to re-install the system without affecting your personal settings and files.
Other than that, I'm not sure what you may mean.

---

### Post by SchwinnSj on 2011-06-18
I was actually responding to oldfred. I believe he was reccomending setting up a small (i used 8 gb) /boot partition and then / (root) partition for the files. But after trying that it gave me "geom error" without even making it to grub. So maybe i should be trying the small  /boot and then /home?
And the issue he was refering to was old computers innability to read after a certain point on large hd's due to old bios. But i'm tenativly thinking thats not the issue

---

### Post by Quackers on 2011-06-18
I wouldn't want to advise on these matters for the reason that a Mac may need a separate /boot partition (probably does). I wouldn't think that a separate /home partition would cause any problems, but in all honesty, I would be guided by advice from the Apple Users section of the forum in all these matters.
I just don't have the necessary experience to advise properly.

---

### Post by drs305 on 2011-06-18
> **SchwinnSj said:**
> 
And the issue he was refering to was old computers innability to read after a certain point on large hd's due to old bios. But i'm tenativly thinking thats not the issue

You can check this during boot by entering the BIOS setup and checking the reported drive size. If it reports a drive size of approximately 137GB  your BIOS is probably facing this issue. 

If the system can boot, the OS will see the entire drive because the OS is capable of that - so it is not an accurate indicator of whether the BIOS is limited or not.

---

### Post by SchwinnSj on 2011-06-18
Where would that be under the bios setup? I don't see any real information about hard disk sizes? Excuse my ineptitude.

---

### Post by SchwinnSj on 2011-06-18
Ah. Under IDE configuration it shows the two internal hard disk size. But it doesn't show the external that i'm using in that menu. So it looks like I'll just assume the size is limited until proven otherwise. That still leaves "geom error" as a problem though. Any ideas on what that could be?

---

### Post by oldfred on 2011-06-18
If you are doing a separate /boot it only needs to be 100 or 200MB depending on how many kernels you want to keep. This would be if you have a very large windows install taking most or all of the 137GB. 
But I do not recommend that for windows either. It can be a lot smaller and then have a shared NTFS partition for data you may want in both systems.

I prefer just to keep / (root) at 10GB  and keep it entirely inside the 137GB limit. Then /home and/or shared NTFS can be beyond limit without issue.

---

