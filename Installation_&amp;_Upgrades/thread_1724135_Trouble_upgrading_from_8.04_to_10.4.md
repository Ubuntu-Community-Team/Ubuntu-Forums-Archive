---
title: "Trouble upgrading from 8.04 to 10.4"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by connundrummer on 2011-04-07
I got a really bad virus on my main computer and decided I should just install Ubuntu like I previously had installed on a laptop.

Anyway, I used an old 7.10 install disk that I usually use and I upgraded from 7.10 to 8.4 LTS (that went off without a hitch) ,but when I upgraded from 8.4 LTS to 10.4LTS the install hung up at one point. The system was stuck 7 minutes from completion trying to set up the rsyslog. I left the dialog box up for 3 hours to no avail.

I proceeded to reformat the drive to try again and it ended the same way. I currently have the system with the install dialog up and stopped at the setting up of the rsyslog.

here is a picture of the install window
[IMG]http://upload.willhost.it/1/tuoa.png[/IMG]

Please leave suggestions! 
Thank you!

---

### Post by Quackers on 2011-04-07
Welcome to UF.
Did you manually run the sudo dmraid command?

If you have already re-formatted, I presume that you are now trying a fresh install of 10.04 from the live cd? Is that correct?

---

### Post by connundrummer on 2011-04-07
Hello,:D

Yes, my brother just entered the command in the window after doing a vague search on how to configure raid (Do not know what he was thinking).

Yes, I used an old 7.10 live disk to install Ubuntu.

Ps. Thanks

---

### Post by Quackers on 2011-04-07
If you are using a Distribution Upgrade, it seems that you have not re-formatted the drive.
Are you using a raid array? If you are, that last command removed raid metadata from your sda drive.

---

### Post by connundrummer on 2011-04-07
I used G-parted to reformat the drive while Ubuntu was running on a live Disk to reformat.
After that reformat, I let the Install utility use the whole disk.

No, I have my raid controller disabled and my second drive is unplugged.

---

### Post by Quackers on 2011-04-07
Maybe I'm missing something here :-)
If you have re-formatted the drive, there is nothing on it.
If there is nothing on it, there is no 8.04 to upgrade, yet your screenshot shows an upgrade in progress.
I would have thought that you would be running an install of 10.04 on an empty disc, not an upgrade.

---

### Post by connundrummer on 2011-04-08
Sorry for the confusion!

The process went as follows

[LIST=1]
[*]virus
[*]Ubuntu 7.10 running on live disk
[*]Used G-Parted to Reformat drive
[*]Ran the install (used the whole hard disk no problems)
[*]Used Update manager to upgrade from 7.10 to 8.04 LTS (no problem)
[*]Use update manager to upgrade from 8.04 LTS to 10.4 LTS
[*]after downloading updates, the install hangs on "setting up the rsyslog"
[*]use a hard reset that ruins everything
[*]try #2-7 again same results happen
[/LIST]

---

### Post by Quackers on 2011-04-08
Ah, I understand :-)  Thanks for the clarification.
I'm afraid I can offer no information regarding the rsyslog error. I have not seen that before and cannot make any suggestion as to what it means.
What I would suggest is to download the 10.04 iso file and burn the image to disc, then do a fresh install.
Obviously you would first need to backup your home folder (including hidden files) and any other data that you may wish to keep.

On the other hand, somebody else may come up with advice which would be more preferrable to you :-)
Good luck in your quest :-) 

It's 5am here now, so I must sleeeeeeeeeep.

---

### Post by connundrummer on 2011-04-08
):PGood Night! and Thank You! 

I will try Downloading the .iso over night that sounds like it would work.
I'm just Going to mark this as resolved and if I have any more problems I will make a new post.

Thank you!:D

---

