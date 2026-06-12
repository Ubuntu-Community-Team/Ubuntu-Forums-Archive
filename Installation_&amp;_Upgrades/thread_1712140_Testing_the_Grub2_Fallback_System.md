---
title: "Testing the Grub2 Fallback System"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by jb.transfer on 2011-03-22
Hi,

I was searching for a detailed description about Grub's Fallback System. I want to test the fallback
opportunities but couldn't find what kind of errors the "fallback" will handle.
I know that it can handle grub errors and os errors. However I want to know exactly what
kind of grub and os errors in order to create a test scenario.

I have the three partitions on a SSD each with its own ( actually the 2nd and 3rd are clones of the
first partition made with rsync)  Xubuntu System on it.

I hope somebody can give me link where I can obtain a detailed description of the grub2 fallback system.

Thx jb


PS: I've found the docs about grub2 in the forums but they don't contain enough information.

---

### Post by Quackers on 2011-03-22
Welcome to UF :-)
I'm not clear on what it is you want to test, nor what "fallback" system you refer to.

---

### Post by jb.transfer on 2011-03-22
Grub2 offers the opportunity to "fallback" to another menuentry if the first one fails.
According to the grub2 documentation here: [http://wiki.ubuntuusers.de/grub_2/skripte](http://wiki.ubuntuusers.de/grub_2/skripte)
(sorry in german) this feature of grub can handle grub errors and os errors in order
to automatically boot another entry.

I removed the kernel of the first partition with grub2 configured with fallback functionality.
The result was the loader couldn't find a kernel and stopped at the grub prompt.

---

### Post by Quackers on 2011-03-22
Are you getting to a grub menu?
Does that grub menu have a recovery option? That's the fallback option I assume you are talking about?

---

### Post by jb.transfer on 2011-03-22
Yes, normal operation is fine. I do not hide the boot menu.
The other entries are accessible and boot just like I want.

After restoring the kernel for the first partition I can boot
as before.

I can manually choose another kernel/entry but  I want
grub to automatically choose another kernel/entry if one
of them fails to boot.

What I need is detailed description of this functionality and
the use case it covers.  :-k


PS: The fallback system is controlled via grub.cfg, /etc/default/grub
and an additional script which resets the counter of grub.
If you do not choose an entry manually at boot it should fall back
to another entry if the first one fails.

IT HAS NOTHING TO DO WITH THE RESCUE ENTRY OF THE GRUB MENU

---

### Post by drs305 on 2011-03-22
I haven't documented the 'fallback' setting in my threads as there isn't any documentation yet in the manual. 

After Natty is officially released I'll add some notes about it. Apparently the fallback is used a bit differently in Natty (1.99) vs Maverick (1.98).

Without testing it myself, if using the 'fallback' setting I would use the *title* of the fallback entry rather than a numeral. [COLOR="DarkRed"](<< EDIT: Perhaps not, see next entry).[/COLOR] Especially with Natty, the default numbers are a bit problematic with the introduction of the submenu. Using the exact title may prevent problems in that area.

I'll try to experiment with fallback today and post here if I come up with anything substantive.

---

### Post by drs305 on 2011-03-22
Update: I've done some testing in Maverick and the current Grub 1.98.

I added this as the last line in /etc/grub.d/40_custom:
> set fallback=4
'4' is an older kernel (and remember to start counting menuentries from 0).

I ran update-grub and *then* renamed the default kernel so it would fail. The backup entry (4) booted.

When I tried it with the exact title, which I thought would be a better solution, it would not work. Only the menuentry number worked for me.

I was not able to add a workable fallback entry into /etc/default/grub.

Anyone who would like to confirm or refute these findings in their Maverick setup is encouraged to do so. I won't document it anywhere else until others have similar results.

---

### Post by Quackers on 2011-03-22
Thanks for that, drs305.
Something new to play with :-)

jb.transfer, I wasn't aware of its existence! Nice :-)

---

### Post by drs305 on 2011-03-22
On a whim, I tried adding the exact menuentry in grub.cfg and it worked:
> set fallback='Ubuntu, with Linux 2.6.35-23-generic'

While I don't advocate editing grub.cfg, the exact title did work as a fallback in this case.

---

### Post by jb.transfer on 2011-03-23
Thank you very much [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945"). I've tested and it is working.


In /etc/grub.d/40_custom I put on the last line:

> set fallback=2

I renamed the kernel of the first entry and voila, it boots off the second entry.
Next I will check if it works with title names. I will also check if I can specify more
fallback entries than two and post the results.

Then I need to get rid of the Rescue Systems which appears. I want the system
to boot up as "normal" ( the user shouldn't notice that there is something wrong )
until the system is booted in the gui/xdm.

Btw why shouldn't I edit the grub.cfg? OsProber is not working properly at my site
so I have to edit grub.cfg by hand. If this last question is too much off topic please
ignore.
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")

---

### Post by Quackers on 2011-03-23
The problem with editing grub.cfg is that every time update-grub is run, or an update to grub is run via updates, it over-writes the changes that you have made.

---

### Post by jb.transfer on 2011-03-23
I've tested with the following settings in /etc/grub.d/40_custom:

> set fallback=2 3

I renamed the the kernels of the first and second entry.
     => System boots the 3 entry.

@Quackers
Glad there seems to be no other reason. I was fighting with this already.
'grub-mkconfig' doesn't write the correct UUIDS of a clone on another
partition into the grub.cfg. Therefore I have to edit the grub.cfg by hand.

To make clear:
I did an 'rsync -avxH' to clone the first partition to the third partition on
the same harddisk. After running grub-mkconfig there are wrong UUID
inside the entry for the synced/cloned partition. I have read that this is
a bug. However I couldn't find a way to troubleshoot this and manually
edited the grub.cfg.

---

### Post by jb.transfer on 2011-03-23
> **drs305 said:**
> On a whim, I tried adding the exact menuentry in grub.cfg and it worked:


While I don't advocate editing grub.cfg, the exact title did work as a fallback in this case.


I have tried but it doesn't like the title. I will make some further tests using titles later.

I put the title of one entry into 40_custom according to drs305 description:
> set fallback='title'For now it is more important to me to find out what different kind of errors can be handled
by grub's "fallback system". Also I want to control what the system does after booting
a fallback entry and if the systems boots from the default entry after fixing.

---

### Post by drs305 on 2011-03-23
If anyone gets the 'title' method to work in other than directly in grub.cfg I'd like to know.

I also haven't been able to use more than one entry in the fallback setting.

Regarding the UUIDs, if you still have duplicates you can change the UUID of the clone with tune2fs:  
```
sudo tune2fs -U random /dev/sd**XY**
```

---

### Post by jb.transfer on 2011-03-24
@drs305

I tested 'grub-mkconfig' before and after the use of 'tune2fs -U'
Sure the UUID of the partition has changed BUT

> 
This is how the entries of the synced partition look in grub.cfg.

search --no-floppy ... --set xxxxx-yyyyy-zzzzzz
linux /boot/vmlinuz root=uuid=xyxyxy-yzyzyz-zxzxzxzUnlike the entries for first partitions the UUIDs, which have matchin uuids for
these two lines, only the UUID of the 'search' line is correct in the entries
of the other partitions.

EDIT: I've read somewhere that this is a bug of grub2. However I think this is off topic
and I've planned to open an extra thread for it.

---

### Post by drs305 on 2011-03-24
> **jb.transfer said:**
> 
Unlike the entries for first partitions the UUIDs, which have matchin uuids for these two lines, only the UUID of the 'search' line is correct in the entries of the other partitions.

EDIT: I've read somewhere that this is a bug of grub2. However I think this is off topic and I've planned to open an extra thread for it.

Was the update of grub run from another OS, i.e. *not* the one with the incorrect UUIDs? If so, this may be explainable by how grub updates. 

For other OS's, G2 first looks for a menu.cfg, menu.conf or menu.lst. It will include the OS's main section (for Ubuntu the 10_linux section) pretty much verbatim for that OS's grub configuration file. So if you haven't gone into that specific OS and updated its own Grub, the UUID in the linux line would be incorrect. 

I'm not sure, but I'm guessing G2 may update the search line or add it if it is missing, which would explain why it is correct.

---

### Post by jb.transfer on 2011-03-25
I started 'update-grub' on each system/partition. After that it seems that 'grub-mkconfig'

writes the correct UUID's for each system on the two lines of the 'grub.cfg'.  I will do further

tests on the weekend.

I want to test this with a fresh install. Lets see if I can write a little howto for that issue.

**Thank you very much drs305**. You have saved my weekend. :D

---

### Post by drs305 on 2011-03-25
Having multiple Grub setups is sometimes a bit inconvenient. If you happen to be in your non-default OS when a grub update is found, you can find that it automatically becomes the default grub (and you see its menu on boot).

You can always tell which G2 is controlling the boot by what appears as the first entry (assuming you don't have a custom menu first). And if the controlling G2 does change all you have to do is boot back into your desired OS and run "sudo grub-install /dev/sd**X**".

---

### Post by jb.transfer on 2011-04-05
> **drs305 said:**
> Having multiple Grub setups is sometimes a bit inconvenient. If you happen to be in your non-default OS when a grub update is found, you can find that it automatically becomes the default grub (and you see its menu on boot).

You can always tell which G2 is controlling the boot by what appears as the first entry (assuming you don't have a custom menu first). And if the controlling G2 does change all you have to do is boot back into your desired OS and run "sudo grub-install /dev/sd**X**".

**Sorry for the long delay.**
@drs305: One big question to me is, what happens when the FS is corrupt and the grub.cfg is not
readable? Will it search for a grub.cfg on another partition automatically?


@ALL
I want to get back to the topic now: Testing the Grub2 Fallback System
[B]
By now we have tested with a removed kernel:[/B]
The Fallback can be used to automatically boot another entry if the default one fails. It is possible
to specify more than one entry.
BUT we could verify this for a removed, missing or renamed kernel ONLY.

**Following a  list of events I want to test - please feel free to complement:**
What happens when the filesystem of an OS is corrupt/not readable?
What If the Kernel hangs during boot process due to bad kernel boot options or defective kernel?
What happens when the init-scripts are hanging?
If X fails, can I automatically reboot the system and tell G2 to use a fallback entry?

---

### Post by drs305 on 2011-04-05
> **jb.transfer said:**
> @drs305: One big question to me is, what happens when the FS is corrupt and the grub.cfg is not
readable? Will it search for a grub.cfg on another partition automatically?


I don't know what is planned but as far as I know it's only going to try to use the listings in the fallback setting.

I'll try some of the other scenarios but my expectations are that G2 once it finds a usable kernel it's going to be done. The reason is that a hung system by definition won't ever get back to the grub menu.

---

### Post by psusi on 2011-04-05
It looks like this will only handle an error loading the kernel ( or initrd ).  One the kernel is booted, grub is out of the picture so can't do anything if there is a problem after that point.

---

