---
title: "best backup method before upgrade?"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by finite9 on 2007-10-29
I do Tar/Gzip/GPG backups every week but just for /home.  I have been waiting patiently for the dust to settle on Gutsy before I upgrade my Acer Aspire 5021WLMi and HP Pavilion dv9297ea (im aware of the HP thread, but my model is not mentioned as problematic, and im writing this post just in case it turns out to be problematic), but I want to do a full backup just before I upgrade.

I have an external firewire disc attached to my "server" (the Acer Aspire), and I wonder if I am able to do the following (I have not tried yet but wonder if this is valid before I start investing time and effort in it):

1. make full backup of HP's / partition by tar'ing root partition across an SSH link to my servers firewire disc.
2. Perform upgrade on HP, without changing partition structure.
3. If I don't like upgrade or something doesnt work and I want to downgrade, then I boot into the new Gutsy installation (assuming it boots), ssh to server and untar my backup onto the root partition of the HP whilst the system is running.
4. Reboot HP again to have fully restored backup of Feisty install.

Is this a valid strategy?  Can I overwrite all Gutsy files whilst Gutsy is running?  What about new files in Gutsy that didn't exist in Fiesty, will these be deleted when tar restores backup?

---

### Post by logos34 on 2007-10-29
Tar is fine for /home, but for / you want to make an image of the entire partition.  Use [Partimage]("http://ubuntuforums.org/showthread.php?t=287522") or **dd** command.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

---

### Post by finite9 on 2007-11-01
that was a good tip.  I will try it, but I have one question... is there any kind of error control?  If I use TAR, then I can check the tar on the server to make sure it really is valid.  Can i use dd with some form of error control just in case some bytes get lost when transferring from the laptop over ethernet to another disc?

---

