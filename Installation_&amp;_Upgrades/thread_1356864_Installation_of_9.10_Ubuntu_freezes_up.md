---
title: "Installation of 9.10 Ubuntu freezes up"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Riverratt on 2009-12-16
Hello All, Newbee here... I am attepting to perform a clean install of Ubuntu 9.10 to an IBM T21 laptop. I have deletd and recreated a primary partition and formatted. I have downloaded ubuntu-9.10-descktop-i386, ISO Recorder and winMd5Sum. I have burned the CD an confirmed 13 folder/objects visible. I can successfully boot from the CD . When I go to install, press F6 to make sure x acpi=off then remove 'quiet splash' from the Boot Option :eed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz -- When I press enter the screen scrolls with information twice and then freezes up. Any Ideas? Do I need to add some additional arguments to the Boot Option?
Any help appreciated.
Thanks

---

### Post by jerrrys on 2009-12-16
do you meet the 
Recommended minimum requirements

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Riverratt on 2009-12-17
Quote: do you meet the 
Recommended minimum requirements


 
Yes I do

---

### Post by itang sanjana on 2009-12-17
Have you check the CD and make sure that it was burned perfectly? [*] Sometimes this could be the problem.

HTH

[*] [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by Riverratt on 2009-12-21
> **itang sanjana said:**
> Have you check the CD and make sure that it was burned perfectly?
[*] Sometimes this could be the problem.
 
HTH
[*] [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
 
The disk appears to burn fine as I have burned it 2 times from original download and once from a new download. The 'Check dosc for defects' will not run on the laptop or my newer XP machine. niether will the 'Try Ubuntu without any change to your computer'. This makes me beleive that the download is corrupt.:confused:
 
Not sure what to do now as I cannot load or try using from even the disk. Hmmm

---

### Post by itang sanjana on 2009-12-21
> **Riverratt said:**
> The disk appears to burn fine as I have burned it 2 times from original download and once from a new download. The 'Check dosc for defects' will not run on the laptop or my newer XP machine. niether will the 'Try Ubuntu without any change to your computer'. This makes me beleive that the download is corrupt.:confused:
 
Not sure what to do now as I cannot load or try using from even the disk. Hmmm

Hmm, perhaps you gotta give this [*] a try.

[*] [https://help.ubuntu.com/9.10/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/9.10/installation-guide/i386/boot-troubleshooting.html)

---

### Post by Yggdrazil on 2009-12-23
I have a similar problem, I got an old laptop on which I'm trying to install 9.10. When I choose Try Ubuntu w/o any change to your computer, Install Ubuntu or Check Disk for defects or any of those, the screen freezes. 

I don't know if I meet the system requirements, I got the computer from my mothers work so I bet it's old but I don't know how old.

It could have something to do with that I have an external cd reader that seems to stop after a while

Any ideas?

---

### Post by Akavashi on 2009-12-23
I had this problem a while back... and I eventually found that if I waited quite a while - eg. up to 15 minutes or so - it would finally resolve itself. Although, this was when I had the white Ubuntu splash (quiet splash) enabled.
Have you tried waiting a while for it? I resolved it to a dodgey DVD drive that I have in my computer.

Dunno if that would help or not, but it's worth trying.

---

### Post by Yggdrazil on 2009-12-23
> **Akavashi said:**
> I had this problem a while back... and I eventually found that if I waited quite a while - eg. up to 15 minutes or so - it would finally resolve itself. Although, this was when I had the white Ubuntu splash (quiet splash) enabled.
Have you tried waiting a while for it? I resolved it to a dodgey DVD drive that I have in my computer.

Dunno if that would help or not, but it's worth trying.

Tried it, it's been doing nothing for two hours now.

---

### Post by Yggdrazil on 2009-12-23
Would using another version help?

---

