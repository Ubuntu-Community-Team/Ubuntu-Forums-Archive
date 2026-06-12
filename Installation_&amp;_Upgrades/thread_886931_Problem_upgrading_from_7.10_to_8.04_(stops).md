---
title: "Problem upgrading from 7.10 to 8.04 (stops)"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by michaelbogardus on 2008-08-11
When 8.04 is installing it's upgrades, it will stop indefinitely at 4 minutes time. This is incredibly frustrating. Any ideas?
I'm upgrading from 7.10, and the last thing it says in the terminal before this freeze is:

Generating locales
  en.AU.UTF-8...

Then it freezes. I'm going to try downloading the Live CD and installing, but I'm not quite sure of the bug that freezes this upgrade.

---

### Post by notoriousdbp on 2008-08-11
I'm having the same trouble upgrading xubuntu from 7.10 to 8.04.  It just stops and does nothing more.

---

### Post by Pumalite on 2008-08-11
Did you have 7.10 fully updated? Did you remove all third parties from your sources.list?

---

### Post by JohnnyC44 on 2008-08-11
A simple search on *generating locales* would have shown you many threads on this topic.  Here's one: [http://ubuntuforums.org/showthread.php?t=865679&highlight=generating+locales](http://ubuntuforums.org/showthread.php?t=865679&highlight=generating+locales)

---

### Post by notoriousdbp on 2008-08-11
I updated 7.10 before running the upgrade and the update procedure disabled the third party sources itself

---

### Post by notoriousdbp on 2008-08-11
> **JohnnyC44 said:**
> A simple search on *generating locales* would have shown you many threads on this topic.  Here's one: [http://ubuntuforums.org/showthread.php?t=865679&highlight=generating+locales](http://ubuntuforums.org/showthread.php?t=865679&highlight=generating+locales)

Thanks for the tip - worked a treat!

---

### Post by starcannon on 2008-08-11
My Dad had the same problem, so I VNC'd in and did a fresh clean install. I had set him up from day one, so fortunately he had his /home directory on its own partition, this makes this sort problem nearly frivolous.

I'd give the same advice as a previous poster, check that your:
System->Administration->Software Sources 
are all stock Ubuntu ones.

Check your sources.list file:
```
gksu gedit /etc/apt/sources.list
```
comment out any lines that you manually entered and may not have shown up in the Software Sources gui.
Then:
```
sudo apt-get update
```

Then try rerunning the upgrade.

If it still fails, then if /home is not on its own partition:
[LIST]
[*]Backup the /home directory to another hard drive, or dvd, or several cd's, or USB stick/'s
[*]Verify the data on another machine to make sure its truely and faitfully preserved
[*]Double Check that you backed up everything of importance to you, I recommend just dragging and dropping the entire /home directory over to the other media, can't miss much of anything that way.
[*]Finally once your sure your important data is backed up, do a fresh clean install, being sure to manually partition the hdd duing the wizard and putting /home on its own partition, this will save headaches in the future.
[/LIST]

If however you already have /home on its own partition, then:
Simply do a clean install, when you get to the manual partition editor, be sure to set the file system and label /home, do not format /home, use the SAME EXACT login name and password as you have always used.
Set the file system and label for root "/" being sure to format it.
Don't bother editing swap, its recognized and used as such already.
Thats it, when you log in your desktop will look like it ever did,(with exception of any 3rd party apps that you may have had running, like viz. Avant Window Navigator, Compiz Settings Manager, and so forth and so on)

If you've read this far, I would also take time to recommend that even if your able to get the auto-upgrader to do its job, now would be a great time to set up /home on its own partition, a bit of work now backing things up and doing a fresh clean install with /home on its own partition could save you a lot of time later down the road. Anyway, GL and let us know how you get on.

Cheers,
Starcannon

---

### Post by michaelbogardus on 2008-08-11
Thanks for all the help. I just reinstalled Ubuntu 7.04, and then downloaded the Live CD for Hardy Heron. Right now I'm on a nice, clean install of the latter. 
I'm impressed by the technical prowess of the forums, and hope one day I'll be able to offer such advice. 
Cheers,
Mike

---

