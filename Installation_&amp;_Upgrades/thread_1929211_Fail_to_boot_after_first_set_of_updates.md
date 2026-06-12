---
title: "Fail to boot after first set of updates"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by cromat on 2012-02-21
On my desktop machine I have been running Mint 12 because it has gnome 3 as the default.  Now that I can get 11.10 with gnome 3 I was going to switch back to plain ubuntu (I know they are essentially the same).  However, I figured id give unity another shot.  Long story short, install goes fine, I install latest ati graphics drivers and configure my 3 monitors. Run the 308 or so updates I don't have and reboot.  So far so good on boot, it sits there I never get a login page nor a command prompt to indicate that there was an issue loading X.  However this same process works on mint any suggestions.

Intel Quad-Code, 708I MOBO, Corsair Force3 SSD, ATI 5870 with 3 monitors 1920x1200.  Any thoughts, this is really bugging me as I have run 10.10, 11.04 without issue as well.

---

### Post by cromat on 2012-02-22
Some more info on this, it looks like it a patch from the Debian base that has been pushed to the ubuntu repositories. I installed pure debian last night and same issue when running on an SSD.  I install ubuntu to a spare 7200rpm drive and I had no issues.  Does anyone know of any defect or another thread discussing issues running what appears to be SSD + ATI?

---

### Post by roelforg on 2012-02-22
If you press CTRL-ALT-F1, does it give you a login screen for a terminal?

---

### Post by cromat on 2012-02-22
No it doesn't tried that and several other commands suggested on the Linux Mint Debian Edition forums.  I can confirm it is occurring in both Ubuntu 11.10 and Linux Mint Debian, but not with Linux Mint 12 (based on Ubuntu 11.10 binary).  So it would seem it is an issue with the combination of the hardware I am running.

Here is what I did:
1. Install 11.10 on SSD, then ATI Graphics, then Updates, and broken on boot
2. Install 11.10 on SSD, run updates, reboot works great, install ATI, reboot broken.
3. Install 11.10 on HDD 7200rpm, then ATI Graphics, then Updates, works on reboot.
4. Install Linux Mint Debian on SSD get ATI graphics, then updates (assuming they all worked tried this twice and had an issue with one of the updates failing), reboot and broken.
4. Install Linux Mint 12 on SSD, then ATI Graphics, then Updates, and on reboot no issues, this is what I have been running for the sake of being able to run linux on this machine.


Did I miss some combination?

---

### Post by roelforg on 2012-02-22
Give me some insight into what's "broken".

---

### Post by cromat on 2012-02-22
Again, it won't boot, I get to grub hit enter goes through what appears a normal boot but all I have is a black screen, CTRL+ALT+F1 doesn't give me a terminal or anything, restarting the machine doesn't help either.

---

### Post by roelforg on 2012-02-22
> **cromat said:**
> Again, it won't boot, I get to grub hit enter goes through what appears a normal boot but all I have is a black screen, CTRL+ALT+F1 doesn't give me a terminal or anything, restarting the machine doesn't help either.
I need to know exactly what the machine does;
do any kb-leds blink?
does any text appear?
does it make weired sounds?
etc.
Your description is rather vague.

---

### Post by cromat on 2012-02-22
> **roelforg said:**
> I need to know exactly what the machine does;
do any kb-leds blink?
does any text appear?
does it make weired sounds?
etc.
Your description is rather vague.

No text appears, no odd sounds.

All 3 screens go black (but act like there is a signal sending black as they don't go to standby).

The hard drive light is always on when this is occurring.  Nothing else is out of the ordinary.

I though maybe it just locked up on boot but several restarts later still the same. It appears to not respond to any keyboard keys either.

---

### Post by roelforg on 2012-02-22
> **cromat said:**
> No text appears, no odd sounds.

All 3 screens go black (but act like there is a signal sending black as they don't go to standby).

The hard drive light is always on when this is occurring.  Nothing else is out of the ordinary.

I though maybe it just locked up on boot but several restarts later still the same. It appears to not respond to any keyboard keys either.
Give it 30 min before rebooting; i suspect fsck is checking your hd.

---

### Post by cromat on 2012-02-22
Any reason why this would occur on an SSD?  I can give it a shot but really curious why that is?

---

### Post by roelforg on 2012-02-22
> **cromat said:**
> Any reason why this would occur on an SSD?  I can give it a shot but really curious why that is?
The SSD is only one of the may components in a pc that determine the max speed of loading apps.
Keep in mind that init is starting several daemons at the same time; it just takes time.

---

### Post by cromat on 2012-02-22
> **roelforg said:**
> The SSD is only one of the may components in a pc that determine the max speed of loading apps.
Keep in mind that init is starting several daemons at the same time; it just takes time.

Your previous message said give it 30 minutes....my Linux Mint boot is in 8 second why 30 minutes or did you mean 30 seconds. I left it once for 10 minutes and nothing.

---

### Post by roelforg on 2012-02-22
> **cromat said:**
> Your previous message said give it 30 minutes....my Linux Mint boot is in 8 second why 30 minutes or did you mean 30 seconds. I left it once for 10 minutes and nothing.
As the HD/SSD's get bigger, fsck has more work to do.
When fsck has more work to do, fsck needs more time.

---

### Post by cromat on 2012-02-22
Alright I'll give it a shot but fsck on a 60 gb ssd shouldn't take 30 minutes that is down right absurd.

---

### Post by roelforg on 2012-02-22
> **cromat said:**
> Alright I'll give it a shot but fsck on a 60 gb ssd shouldn't take 30 minutes that is down right absurd.
40gb hd: 20min
60-40=20
40/2=20
20/2=10
20+10=30min=60gb

---

