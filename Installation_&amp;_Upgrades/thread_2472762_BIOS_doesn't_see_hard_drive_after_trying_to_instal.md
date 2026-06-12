---
title: "BIOS doesn't see hard drive after trying to install 22.04"
date: 2022-03-11
forum: Installation &amp; Upgrades
---

### Post by 98cwitr on 2022-03-11
Perfectly good and working SSD with 20.04 on it. Popped in my bootable Ubuntu 22.04 (live works fine) and it couldn't find the drive. Checked BIOS and poof, no HDD listed. Tried another drive and the same thing happened. Tried slaving drive up using a sata to USB cable, Windows nor linux sees it.

---

### Post by oldos2er on 2022-03-11
[Sorry, delete]

---

### Post by grahammechanical on 2022-03-11
I am a bit confused. Please confirm. This "perfectly good and working SSD with Ubuntu 20.04 on it" is it booting and loading Ubuntu 20.04?

If the SSD is not booting and the BIOS cannot see it and Disks utility and GParted in a Ubuntu 22.04 live session cannot see it, then perhaps it is not seated correctly or it is not in fact a "perfectly good and working SSD." 

I cannot understand how it can be booting if the BIOS/UEFI settings utility cannot see it. I only recently purchased a laptop with a UEFI motherboard and an SSD so I have little experience of these systems. Is it possible to disable an SSD in the UEFI settings utility? I do not know.

I am just sharing some thoughts. Regards

---

### Post by oldfred on 2022-03-11
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

And similarly post link to this report which documents your hardware.
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
wget -N -t 5 -T 10 [https://github.com/Mafoelffen1/system-info/raw/main/system-info](https://github.com/Mafoelffen1/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info

---

### Post by breakdaze on 2022-03-14
Definitely get that bootinfo summary posted. Also, can you please elaborate on the part about "trying to install 22.04." I'm unclear as to how far you got with the trying process, which flavor of Ubuntu, if you picked the standard options. If you started the process and it started installing a fresh 22.04 on the same drive that had 20.04 before, or... ? Did you do any physical unplugging of the SDD, and what's the make and model of the SSD, and PC? What kind of bootable live media, USB pen drive, or DVD? What's the other drive you tried? Have you tried the drive on another computer, if available? Can you post a link to a photo of your BIOS screens?

EDIT: In General, when troubleshooting, divide and conquer. In other words, for hardware, use a known good computer to test a fixed disk, for example. 

In your situation, where the BIOS doesn't show 2 drives, it begs the question, have the SATA settings in BIOS changed?  Also, it is possible the SATA controller on the motherboard died, that is, motherboard hardware failure. If you meant the UEFI entry in the UEFI (BIOS) firmware settings, that's different. If your firmware really can't detect the SATA drives, you could also try writing down or taking pictures of your current firmware (UEFI or BIOS) configuration and then resetting it to factory defaults to see if that helps. But again, first re-seat connections internally, and/or try new a SATA cable. SATA cables are notoriously flaky.

---

