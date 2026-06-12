---
title: "Boot from cd"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by karmah on 2005-06-03
[FONT=Courier New]Ok, first off i wanna enlighten everyone with the fact that im not a noob at computers, just at linux...so i dont make incredibly nooby misstakes :).

Ok, the problem is that the comp wont find the CD when i try to boot from cd..Only the Ubtunu discs..no others! It worked until the day before yesterday, then it just stopped working. Both CD readers works when in Ubuntu.
No clue of what the problem is, someone plz help!
thx in advance.[/FONT]

---

### Post by mingus on 2005-06-03
Sorry, but I am not totally clear on the question . . .

You installed Ubuntu from the CD, the CD-ROM's work with other CD's, you can boot from some other CD media, but now you cannot boot from the Ubuntu CD only?

---

### Post by karmah on 2005-06-04
No, i can boot from the Ubuntu CD, but no others :( ! I wanna use AGNULA or Windows to make music, but I cant boot from any CD except Ubuntu.

---

### Post by mingus on 2005-06-04
Hmmm . . . that *is* strange.   :? 

I cannot think of anything having to do with either the kernel or Ubuntu that would affect this.  Booting from CD is a hand-off from the BIOS to the boot sector burned on the CD.  And I can't think of anything in the BIOS that would make one bootable CD boot but another one not.  And you indicate there is nothing wrong with the other media.  So sorry, I am at a loss.

---

### Post by karmah on 2005-06-04
Aw damn..I don't feel like formatting my comp when i finally got it the way i wanted it (almost) :'(...well...Ill keep asking around!
thx anyways.

---

### Post by mingus on 2005-06-05
As I thought about this a bit more . . . you indicate that only the Ubuntu CD's will boot now.  You refer to other media that will not boot such as Windows.  What exactly is the Windows media that you are trying to boot from?  When this media is in the drive, does the system at least recognize it as a boot CD and then tries to boot with it, and it fails during this process?  Or does the system not even try to boot with that media?

---

### Post by karmah on 2005-06-06
No, when I press F12 for boot menu and then choose  boot from CD, it just says "Please insert disc, hit F1 for retry or F2 for setup." Or something like it.

---

### Post by mingus on 2005-06-06
sorry, still not clear . . . *what* is it that is running where you press F12 for a boot menu and it says 'insert disc', etc. . . .????  what is *this* program?

---

### Post by karmah on 2005-06-06
BIOS thingie? when you start your comp you're usually able to press an F button to popup bios setup? is there any other way to boot from CD :S ??

---

### Post by mingus on 2005-06-06
The communication here is a bit difficult . . . trying to determine *exactly* what is failing.  Systems display different dialogues thru this process . . . here is an outline of the process, perhaps that will help to pinpoint the problem.

The BIOS loader and BIOS setup are two different programs.  Setup is entered by hitting a key like F1 or F2 or delete, while the loader is running.  Setup is where you tell the BIOS which devices are bootable, and in what sequence the BIOS should check those devices for bootable media.  You need to be sure that in Setup you have configured  the CD-ROM as the first bootable device.  Changes made with Setup need to be saved to the BIOS ROM device, and then the system will reboot.  

The BIOS loader program's last step is to check the boot table configured above, and then look for media in the configured devices, in the sequence defined in the table - if media is found it then looks for a loader program on that media.  If the media (CD, floppy, HDD) does not have a proper loader program where the BIOS expects to find it, the BIOS will move to the next device.

Usually all the user sees is a very quick BIOS dialogue.  If a floppy is configured as a boot device, usually no message is displayed; the system goes straight to boot.  If a CD is configured for boot, usually there is a message displayed like "press any key to boot from CD . . ." and if a key is not pressed, the CD will be skipped.  The dialogue can be different.  Whatever it is, if the BIOS is told to boot from CD and that does not immediately happen, there is an issue with the media.

At the moment, the operating system is not in the picture at all.  It has not been loaded.  So whatever is installed on the HDD does not have anything to do with it.  That is why reformatting would not help.

Most of the time a problem like the one you describe, is somewhere in how the BIOs is configured to boot or with the media itself.

---

### Post by karmah on 2005-06-06
oO...well...I use a Dell and i get to choose from F2 and F12...F12 leads directly to a BOOT SETUP. There i get to choose what i wanna boot from. Then it boots from what i selected right after i hit enter..It can not boot from other discs than the Ubuntu installation disc. It went like this all of a sudden, I didnt change any settings in the BIOS or anything. I have no clue of what to do... :( ..I know that what's on the harddrive doesnt matter until you've booted from it, but this got to have something to do with Ubuntu since its the only disc I can boot from :S

---

### Post by mingus on 2005-06-06
Ouch . . . back to square one.  Since this is a customized Dell BIOS maybe it would be good to ask Dell?

---

### Post by karmah on 2005-06-06
bleh, well if no-one has any useful information to help me out of this. Then I'll call some sucky support-line.
Thx anyways

---

### Post by Ptero-4 on 2005-06-06
[QUOTE=karmah]bleh, well if no-one has any useful information to help me out of this. Then I'll call some sucky support-line.
Thx anyways[/QUOTE]
 karmah. In the BIOS "Boot Menu" when it says press F1 to retry. Has you tried ejecting the CD, inserting it again and when the drive begins to read pressing F1. That may help. 
Mingus, what karmah is talking about is the BIOS boot menu. My sister got an HP and if you press Esc when you turn that PC on a DOS-like menu appears listing all the boot options (CD, floppy, HD, Zip, LAN, USB, etc).

---

### Post by mingus on 2005-06-06
Thx Ptero-4.  I guess that is a little "feature" I haven't come across.

karmah, what this emphasizes is that the problem lies in how this BIOS loader is managing the boot sequence hand-off, or the media itself.  I suppose it's possible that there is something that the Ubuntu install could have done to squirrel this, but it sure seems doubtful.  I wouldn't go re-formatting just yet.

---

### Post by karmah on 2005-06-06
[QUOTE=Ptero-4]karmah. In the BIOS "Boot Menu" when it says press F1 to retry. Has you tried ejecting the CD, inserting it again and when the drive begins to read pressing F1. That may help. 
Mingus, what karmah is talking about is the BIOS boot menu. My sister got an HP and if you press Esc when you turn that PC on a DOS-like menu appears listing all the boot options (CD, floppy, HD, Zip, LAN, USB, etc).[/QUOTE]
Yeah, sure I've tried it, nothing happened.

Mingus: As i said it didnt go malfunctioning after I installed Ubuntu. It was all of a sudden, I had Ubuntu installed and it worked fine. Then it stopped, can not figure out  what triggered this sudden change of mind in my comp.  :|

---

