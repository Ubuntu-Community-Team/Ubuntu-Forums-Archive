---
title: "Feisty upgrade has me bamboozled"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by weemikey on 2007-05-30
OK, I went for the Feisty and the update.  Now I can't even log in, I get the message:
<User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.>
So I press <OK> and after a while I read <Unable to lock the file /home/michael/.ICE authority blah, blah>
I did manage to start a Failsafe Terminal session, but really have absolutely no idea what to do now. On gedit /etc/fstab which a lot of people seemed to be having problems with, I got 

# /dev/hda1   UUID=17d7ed90-8adb-4a44-94c6-8521b39b1d55  / ext3                    defaults, errors=remount-ro    0    1
# /dev/hda5 and its UUID=e8ad17aa-2f2c-4410-a526-def6b81cda1a          none  swap sw   0   0
/dev/hdc     /media/cdrom0   udf, iso 9660, user, noauto   0   0
/dev/cdrom    /media/cdrom1    udf, iso 9660, user, noauto   0   0
/dev/          /media/floppy0  auto    tw,user, noauto    0   0

What would happen if I uncommented my hda1 and hda5?  Would they come alive again?
If I force loaded Edgy Eft again would I lose everything I now have on my hard drive?
I'm doing this messaging by having loaded the Live Cd (Ubuntu 6.06LTS) and using the Firefox browser.

---

### Post by merlinus on 2007-05-30
Try uncommenting the lines.  That is why those partitions are not loading.

/dev/hda5 and its UUID=e8ad17aa-2f2c-4410-a526-def6b81cda1a none swap sw 0 0

I would get rid of 'and its' in this line also.

In fact, if you are using UUIDs, you do not need /dev/hda1, etc.

Here are the lines from my /etc/fstab:

# Entry for /dev/hda7 :
UUID=a961b624-ed15-4878-b66f-bb2d007b74a4 /home ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/hda9 :
UUID=68313a8e-5d21-43d6-b759-099c3f6de0f0 none swap sw 0 0

Good luck!

-merlin

---

### Post by weemikey on 2007-05-30
Well I uncommented those two lines and had another try.
Still getting the <$HOME/.dmrc file is being ignored......>  message, and the <unable to lock the file /home/michael/.ICE authority> message.
Does anyone have any idea at all what I'm to do?
If I reload Edgy will I lose all of my data in /home?  so far it's still there when I check through the failsafe terminal, but who knows for how long.

---

### Post by weemikey on 2007-05-30
Sorry, should have asked this earlier.
Is there a way I can "scrape" all my data on to a CD by using terminal?
You'll have to lead me through it by the hand mind you!
Thanks, Mike

---

### Post by floke on 2007-05-30
You could try deleting the .dmrc and .ice/Xauthority files.
Also delete: .gconf .gconfd .gnome .gnome2 .gnome_private

NOTE: This will reset ALL your gnome settings / configurations etc. But should allow you to boot back in.

---

