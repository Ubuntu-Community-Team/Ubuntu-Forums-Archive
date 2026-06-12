---
title: "Everything stops at &quot;Starting Hotplug Subsystem&quot;"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by ajb on 2006-04-28
Alright.  I've used the search, and lots of people have problems similar to this, but either the solutions there don't work for me or I don't understand them.

My System:

Intel Pentium 4 3.0 GHz
Asus motherboard with ATI Radeon Xpress 200 series card
Realtek HD Audio sound card

Here's whats going on.  I installed Windows XP first, and then Breezy Badger ubuntu.  Everything went fine until it started loading modules.  It got to "Starting Hotplug Subsystem" and stopped.  It sat there for awhile, and eventually the pretty screen with the ubuntu logo was gone and  the last 10 or so modules came onto the screen in white lettering  with a bunch of [ok 's written on the right side of the screen... but not so for 

*Starting hotplug subsystem...  

It just stays on that screen forever.  I'm really bummer because I've never used Linux before and really wanted to try it.

Solutions I've tried which haven't worked:
-Unplug USB devices
-Enabling and Disabling ACPI support in Bios (tried it both ways)
-Creating a new install disk on lowest burn level and tried again.
-recovery mode (text scrolls forever and ever but nothing happens)

I'm open to any suggestions, but I can't type any code into linux because I can't even get that far.  This is my first time using Linux so if you give advice, please tell me exactly what to do.

Thanks...

---

### Post by bluevoodoo1 on 2006-04-28
While it's stalling on Starting hotplug subsystem... you can hit Ctrl+c and the bootloader will skip it. I'm curious to know... if you skip it, does the rest of the loading process work [more] normally?

---

### Post by ajb on 2006-04-28
I Waited until it stopped, and then pressed Control + C ... it didn't move on.  Tried it several more times... no luck :(

---

### Post by ajb on 2006-04-29
Anyone? ](*,) 

What does "Starting Hotplug Subsystem" mean, exactly?

---

### Post by slashird on 2006-04-29
I'm having the same problem - same mobo, P805D processor.

---

### Post by jegsar on 2006-04-30
i have the exact same problem i've tryied on a sony VGC-RA826G and a fairly old compaq about 3 years old maybe 4 anyways i complelty wiped the harddrived deleting all partitions on that and the same thing happens. i have no clue. also 2 of my friend have the same problem.

---

### Post by westvleteren on 2006-05-01
I have the same problem as well. I am running a new Asus A3H laptop. But I had to install windows to come to the forum.
 I will do a search and find out if there any other solutions, and post them here.

---

### Post by westvleteren on 2006-05-01
Ok I did a search and found this link : [http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g/](http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g/)
It seems that other people had this same problem, and tried the solution given in the post (link above), and it worked for them. I will also give this a try. to see if it works on my computer.
Good luck All

---

### Post by westvleteren on 2006-05-01
Ok I went to the link and I tried the things out, but wasnt successful.
Then I tried to race the process loader by hitting "Ctrl C" on a few processes, Just as it started system time clock in the list, and I GOT IN, unfoutunately this does not solve the problem. You must be logged in as root to change settings to prevent this from happening each time you boot. I dont know what to change to fix it, but I hope somebody does. I hope the solved this problem in the new release coming out next week or so.

---

### Post by zolero on 2006-06-26
[COLOR="Red"][SIZE="5"]Hello there! Don't worry Friend. Here comes your solution...[/SIZE][/COLOR]

I own the same **Asus A3H 5010**, and I've have the same problem in Ubuntu Breezy. Your install was good. The prob comes from the soundcard. Good news! It can be figured out! But firstly: why do you don't try Dapper Drake? There isn't such a problem... (only with the headphones, but it can be solved well and quickly :confused: ...)

Soundcard on this notebook is HDA Intel (see [here]("https://help.ubuntu.com/community/ASUS_A3H_5010_Laptop_with_Ubuntu?highlight=%28CategoryDocumentation%29") for more details). :cool: 

Your notebook freezes at **"Starting hotplug subsystem..."** and this mean that your kernel doesn't support the soundcard (can't recognize it), but it isn't blacklisted for jumpin' over at boot process, and it freezes... :evil: 

1.) Reboot and enter BIOS (press F2 during restart), go to sound/modem section and disable it. Restart, ... and it don't freeze anymore (but we have more work to do on :-D )

2.) Open **blacklist** file in gedit as root (type followings in terminal):

          ```
$ sudo gedit /etc/modprobe.d/blacklist
```

and insert at bottom of file:

          ```
snd-hda-intel
```

Check out if it is there a line **snd-alc880** or something like this, and if it is commented in (had a # mark at beginning of the line) or out. If doesn't exist this line, or is commented in, insert/comment it out. Save the file and restart notebook.

3.) Reenable soundcard from BIOS. Now it **won't freeze** during boot-up. But we still have some work to do, because there isn't sound (yet).

4.) Download the newest ALSA driver from [**it's homepage**]("http://www.alsa-project.org").

5.) Remove the soundcard from the blacklist by commenting in line(s) referring to soundcard (put # in front of line(s), then save file). **If U miss this step before workin' on sound driver, this results in failing to enable sound, and U have to repeat all from here.**

6.) Thereafter compile ALSA driver as module in your kernel by followin' theirs [**install and config instructions**]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel").

At this point U need to create some files, identically to KBuel's description [**in this tread**]("http://www.ubuntuforums.org/archive/index.php/t-76307.html") (and don't worry about that KBuel had only SPDIF problem. His notebook is another Asus model, and the sound may working fine on it, excepting SPDIF!) Don't forget to create the file ~soundrc on top of the root filesystem (/), in your home dir, and root's home dir (with identical content and name) described at ALSA-page.

7.) If U've worked correctly, and followed all instructions, U **must get sound** after the next restart.

It wasn't too hard, isn't? Enjoy your music and videos from now \\:D/ ;)  :-D .


If U've decided to use Dapper Drake, this is a good decision. Above I've said that sound is problemless in the new release on Asus A3H, but there is still one minor problem with headphone (SPDIF). To solve this one, just put this line at bottom of your **/etc/modprobe.d/alsa-base** file:

          ```
options snd-hda-intel model=z71v position_fix=1
```

and after saving file, and restarting laptop, problem must be solved.

Cheers, Zolero.

---

### Post by zolero on 2006-06-26
[COLOR="Red"][SIZE="5"]Hello there! Don't worry Friend. Here comes your solution...[/SIZE][/COLOR]

I own the same **Asus A3H 5010**, and I've have the same problem in Ubuntu Breezy. Your install was good. The prob comes from the soundcard. Good news! It can be figured out! But firstly: why do you don't try Dapper Drake? There isn't such a problem... (only with the headphones, but it can be solved well and quickly :confused: ...)

Soundcard on this notebook is HDA Intel (see [here]("https://help.ubuntu.com/community/ASUS_A3H_5010_Laptop_with_Ubuntu?highlight=%28CategoryDocumentation%29") for more details). :cool: 

Your notebook freezes at **"Starting hotplug subsystem..."** and this mean that your kernel doesn't support the soundcard (can't recognize it), but it isn't blacklisted for jumpin' over at boot process, and it freezes... :evil: 

1.) Reboot and enter BIOS (press F2 during restart), go to sound/modem section and disable it. Restart, ... and it don't freeze anymore (but we have more work to do on :-D )

2.) Open **blacklist** file in gedit as root (type followings in terminal):

          ```
$ sudo gedit /etc/modprobe.d/blacklist
```

and insert at bottom of file:

          ```
snd-hda-intel
```

Check out if it is there a line **snd-alc880** or something like this, and if it is commented in (had a # mark at beginning of the line) or out. If doesn't exist this line, or is commented in, insert/comment it out. Save the file and restart notebook.

3.) Reenable soundcard from BIOS. Now it **won't freeze** during boot-up. But we still have some work to do, because there isn't sound (yet).

4.) Download the newest ALSA driver from [**it's homepage**]("http://www.alsa-project.org").

5.) Remove the soundcard from the blacklist by commenting in line(s) referring to soundcard (put # in front of line(s), then save file). **If U miss this step before workin' on sound driver, this results in failing to enable sound, and U have to repeat all from here.**

6.) Thereafter compile ALSA driver as module in your kernel by followin' theirs [**install and config instructions**]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel").

At this point U need to create some files, identically to **KBuel's description** [**in this thread**]("http://www.ubuntuforums.org/archive/index.php/t-76307.html") (and don't worry about that KBuel had only SPDIF problem. His notebook is another Asus model, and the sound may working fine on it, excepting SPDIF!) Don't forget to create the file ~soundrc on top of the root filesystem (/), in your home dir, and root's home dir (with identical content and name) described at ALSA-page.

7.) If U've worked correctly, and followed all instructions, U **must get sound** after the next restart.

It wasn't too hard, isn't? Enjoy your music and videos from now \\:D/ ;)  :-D .


If U've decided to use Dapper Drake, this is a good decision. Above I've said that sound is problemless in the new release on Asus A3H, but there is still one minor problem with headphone (SPDIF). To solve this one, just put this line at bottom of your **/etc/modprobe.d/alsa-base** file:

          ```
options snd-hda-intel model=z71v position_fix=1
```

and after saving file, and restarting laptop, problem must be solved.

Cheers, Zolero.

---

### Post by Cloudy on 2006-06-27
Definitely bookmarking this. I'm having a similar problem just trying to run the live CD on a Sony Vaio PC with stock parts. I get as far as the hotplug subsystem and then it freezes; I've waited up to two hours before for something to happen.

gonna have to try some of the stuff mentioned here when i get home, cheers. helpful topic & responses.

---

### Post by candyraver69 on 2006-07-13
My alienware laptop has the same problem, but my bios doesn't have a sound-card/modem section. The ctrl c thing does nothing for me either. Do you think if I flash bios from windows that I might have more bios options, or is the sound-card fix just for that MOBO?

---

### Post by Cloudy on 2006-07-16
I found that if you blacklist your soundcard it's a nifty temporary solution; however, I have an onboard intel soundcard, don't know about you. All I did was boot into recovery mode and from there add snd_hda_intel and snd_hda_codec to the blacklist file in.. uhh.. one of the .d folders. rules.d? I don't think so.. but anyway..

---

