---
title: "cant install ubuntu 19.10"
date: 2019-11-12
forum: Installation &amp; Upgrades
---

### Post by seekertom on 2019-11-12
fresh ssd on desktop pc. installed 18.10 from live dvd with no problems. followed same procedure to install 19.1 from live dvd. it boots, I say install, it reads dvd for a few mins then quits saying oh no! something has gone wrong...

same thing on diff hd.
what's going on?
st.

as of 11/14/19
ok. downloaded fresh copy of 19.10, burned iso to dvd, still getting same error on install. Im using 19.10 for desktop amd 64bit, download on hp prodesk pc running ubuntu 18.1 now with no problems. 

disks app shows ssd has 2 partitions, part 1, 537mb fat efi system, /dev/sda1, mounted at /boot/efi, and part 2, 119 gb ext4, /dev/sda2, linux filesystem, ext4, mounted at filesystem root.

after booting from new 19.10 dvd, menu comes up, I select install ubuntu and it takes off, runs a few mins, then dies.

does this additional info on what I'm doing help anyone see what I'm doing wrong???
thanks, t

as of 11/27/19
what I discovered... good chance the original hdd install was not correct. it looked like the uefi partition was not where it ought to be.
my final solution was to give up on trying to repair the system having 18.04.3 plus 19.10, and se5ttled for a fresh install of 19.10 and let it go at that.
wish i understood more about it, but time has become a factor.

thanks to everyone for you input.
st

---

### Post by deadflowr on 2019-11-12
Run the *check disk for defects* feature in the iso.
Or did you already?

---

### Post by seekertom on 2019-11-12
did not chk the dvd, but will do so now. this is the third copy im using, however. prev 2 copies same issue...
thx, t

---

### Post by seekertom on 2019-11-12
feelin dummy rite now. i know ive see the option to check the disc, but unsure now how to get there again.
i just rebooted on live dvd and it did the try ubuntu ok, ended at desktop. i dint see the option to check disk this time.
i suppose even tho it loaded to desktop ok, there may be more files used to install fully, which may be crunched. dunno.
so, where is the check disk option?

---

### Post by deadflowr on 2019-11-12
Is there a check disk for defects in the boot menu?
Where Try Ubuntu and Install Ubuntu are listed?

---

### Post by uRock on 2019-11-12
You should be able to see it in this screen.

---

### Post by guiverc on 2019-11-12
On some boxes you need to press a key for the menu to appear, if you see a keyboard-in-rectangle and person-in-circle quickly hit a key and the menu appears.   Your actual box BIOS/UEFI setup will control if you need to do this, or it appears without keystroke.

fyi:  *Ubuntu releases are *yy.mm* in format, there was no 2019-January release of Ubuntu.*

---

### Post by seekertom on 2019-11-12
i followed your helpful instructions, ran the discchk and it reported no errors.
thanks, t

---

