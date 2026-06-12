---
title: "&quot;Partition Table&quot; problem installing Ubuntu on a drive (from a Mac) on a Dell laptop"
date: 2021-08-08
forum: Installation &amp; Upgrades
---

### Post by freedonspark on 2021-08-08
[LIST]
[*]pulled an SSD storage drive out of a broken mac (OSX High Sierra)
[*]Now, when I start the computer normally, it quickly goes to a black screen with these words at top "Invalid partition table!"
[*]Now, in the BIOS menu for UEFI BOOT, there is a new item titled "ubuntu." I select ubuntu which starts the new Ubuntu on the SSD.
[*]When booting again into the Live Ubuntu USB and going to GParted, **[you see 2 partitions on the SSD in my screenshot]("https://drive.google.com/file/d/1OmUNT-CRDK8WaWd2VJxZuacMS8HDMLOu/view?usp=sharing")**
[/LIST]
[IMG]https://drive.google.com/file/d/1OmUNT-CRDK8WaWd2VJxZuacMS8HDMLOu/view?usp=sharing[/IMG]
After this boot/format problem is solved, I will need to also install Windows 10 on the SSD for dual boot. But in: 
GParted > Device > Create Partition Table, there is no MBR option in the pull-down for "Select new partition table type." I thought MBR would be necessary to install windows for dual boot.

---

### Post by grahammechanical on 2021-08-08
I am confused. You take an SSD out of a computer. Now when you start that computer you get  a "invalid partition table" message. Is that the case? Or,

You put the SSD in a second machine and it gives you the "Invalid partition table" message. Is that the case?

Ubuntu is on this SSD and in the second machine's UEFI settings you get a new item titled "Ubuntu." That is as it should be. Have you set the UEFI boot order to boot from this SSD with Ubuntu on it? What other drives do you have in this second machine? 

I disagree with you. For Windows 10 we need a GPT partition table. That is my understanding. Not MBR.

My motherboard is BIOS not UEFI and I can use GParted to set a drive's partition table as either MBR or GPT. I would not be surprised if on a UEFI motherboard GParted only offered GPT for the partition table. I have not tested this.

Your screenshot does not indicate what partition table is on the SSD. I suspect that it is GPT. Installing Ubuntu on to a GPT drive in a BIOS motherboard will produce a BIOS boot partition as well as an EFI system partition. I do know that to be true. Your SSD only has an EFI system partition.

Regards

---

### Post by oldfred on 2021-08-08
Mac use gpt with UEFI booting and have for years.
Windows changed to UEFI boot from gpt partitioned drives in 2012.
But a user can boot in BIOS mode can install to MBR with Windows, That will erase drive when it is converted.
If system is UEFI, you need to boot installer in UEFI boot mode.
Both Windows & Ubuntu install in the same mode as you boot installer, so boot installer in UEFI boot mode. And then make sure system UEFI settings are to boot in UEFI mode, not old BIOS/Legacy/CSM mode.

---

### Post by freedonspark on 2021-08-08
Thanks for the attention.
I took the SSD out of a mac and put it into a Dell to replace the boot drive.
Then, I installed Ubuntu on the SSD.
The Dell now give me the "Invalid partition table" message.
The Dell UEFI settings now give me a new item titled "Ubuntu."
There are no other drives in this Dell. I have not changed boot order.
"For Windows 10 we need a GPT partition table." Understood.
Device info shows both partitions on the SSD are GPT.

In the BIOS Setup, I changed the Boot List Option from "Legacy" to UEFI which canged the boot sequence from the normal list to just the single "Ubuntu" (with the option to add more.)

The dell boots into ubuntu when pressing the power button now.
THANK YOU FOR THE HELP!

---

### Post by MAFoElffen on 2021-08-10
So this is "Solved" right? Please thinkabout other's who may have similar problems, by marking this thread as solved in the Thread Tools (upper right) so they can find your solution.

---

