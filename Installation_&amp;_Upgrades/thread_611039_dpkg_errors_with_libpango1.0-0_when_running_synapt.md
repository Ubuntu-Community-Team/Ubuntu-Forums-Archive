---
title: "dpkg errors with libpango1.0-0 when running synaptic"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by gaiag on 2007-11-12
Help! I cant get my packages to update.

Here's the error I receive:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 10384 package 'libpango1.0-0': invalid package name (character ':' not allowed (only letters, digits and characters '-+.+')) 
: Sub-process /usr/bin/dpkg returned an error code (2)

any thoughts on how to correct this problem and what could've caused this error?

---

### Post by Pumalite on 2007-11-12
Run:

sudp dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

Report back.

---

### Post by gaiag on 2007-11-12
i've tried a few steps and commands you listed below, which didnt work. however, for the sake of getting support I tried what you listed below...

when i use run the first step:

sudo dpkg --configre -a

i get the same error message

sudo apt-get update does not return any errors whilst reading the package list.

sudo apt-get upgrade returns errors, so i added -f to the line. however, regardless of the -f option i still receive the same error i stated earlier.

---

### Post by Pumalite on 2007-11-12
Have you tried:

sudo apt-get install -f

---

### Post by gaiag on 2007-11-12
yep, i tried that too... still returns that same error message.

i tried apt-get commands to get this working, but no avail. tried:
sudo apt-get remove libpango1.0-0
sudo apt-get source libpango1.0-0
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get check -f

all of those commands have failed to correct my busted package. 

it's just odd that this is a persistent problem. i didnt have any installation errors at any point, but for some reason this one bloody package is preventing me from doing anything with apt-get. 

sigh

any other thoughts?

thanks for helping btw.

---

### Post by Pumalite on 2007-11-12
Try this:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by gaiag on 2007-11-12
i just did an apt-get check, which returned something interesting:

The following packages have unmet dependencies:
     libpango1.0-0: Depends: libpai but it is not installable. 

i then tried: sudo-apt-get install libpango1.0-0, which returned a line telling me to run apt-get -f install to correct problems.

i then entered sudo apt-get -f install, which returned another set of messages stating that package lists, dependency tree, state info and correcting dependencies were "done". i was then prompted to unpack an addition 101mb, which i said yes to. again, still presented with same dpkg parse error

how valuable is this file to my systems state? can i gedit the status file and comment out, or remove the problematic line?

---

### Post by Pumalite on 2007-11-12
Yes. Go to /var/lib/dpkg/status and you can fix it there ( from not installed to 'installed...ok...installed')(it's cheating, but gets you out of the hole)

---

### Post by gaiag on 2007-11-12
ok -- i ran the command you suggested: sudo dpkg --remove --force-remove-reinstreq <packagename>

when running that command, i receive this error:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 10384 package `libpango1.0-0':  invalid package name (character `:' not allowed (only letters, digits and characters `-+._'))

so, could it be the file name causing the problems? how do i go about correcting that, if it is indeed the case? just a simple cp to another file name?

---

### Post by gaiag on 2007-11-12
> **Pumalite said:**
> Yes. Go to /var/lib/dpkg/status and you can fix it there ( from not installed to 'installed...ok...installed')(it's cheating, but gets you out of the hole)

oddly, it said 'install ok installed' on the line. there's also another line on 10384 that has a ":" at the beginning on the line, could that be my problem?

i just find odd that the system is treating this like a name issue, which it might be.

---

### Post by Pumalite on 2007-11-12
Try deleting the offending item (".")
Backup the file first.

---

### Post by gaiag on 2007-11-12
> **Pumalite said:**
> Try deleting the offending item (".")
Backup the file first.

yep -- did that. then ran apt-get update and apt-get install -f... this time i was presented with other errors in the file, simlilar to the ":" name issue. seems like some bits lost their place. 

my eyes are red, and it appears i have more editing to do (which if to be completely unecessary)

i'll try again tomorrow morning and post back what happens.

just curiously wondering why this happened off a fresh install? i can see the files being corrupted, but what else would a user do? re-install?

thanks!

---

### Post by Pumalite on 2007-11-12
Sometimes you have to reinstall, but let's wait and see if you can fix tomorrow first. Edit out all you have to. Then we'll see.

---

### Post by gaiag on 2007-11-13
> **Pumalite said:**
> Sometimes you have to reinstall, but let's wait and see if you can fix tomorrow first. Edit out all you have to. Then we'll see.

well, i'm at that point. i guess my office lost power last night; came in to find the test box sitting at a promp. tried rebooting and going into a recovery mode, which didnt work. 

so, given the fact i've had numerous errors post install, plus these new issues, i've decided to rebuilt the system. at this point, i'm fighting an uphill battle, and i find it more conducive to just start over.

thanks for your help Pumalite

---

### Post by Pumalite on 2007-11-13
You are welcome. Good luck.

---

### Post by gaiag on 2007-11-14
well, apparently it was the hardware in my system. i swapped out the cd rom with another one. still had a clean install, but updating did not present any errors, oddly enough. 

i was able to get a clean install of 7.04 on my system, then manually update to 7.10 through synaptic. i determined it was the cd-rom as I used the old cd-rom in a new system that i wanted to put kubuntu on. proper installation, but tons of errors when trying to update kubuntu. after removing that cd-rom and starting with a fresh install and new hardware i did not encounter any problems.

lesson learned:

even after a clean, fresh install, hardware problems prevented the system from functioning properly. i believe the sys files were not copying properly from the busted cd-rom. odd, just very odd. i would've expected errors during pre install, not afterwards in post.

---

