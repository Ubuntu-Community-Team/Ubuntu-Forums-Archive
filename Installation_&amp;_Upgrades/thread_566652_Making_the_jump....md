---
title: "Making the jump..."
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by derekr44 on 2007-10-03
Ok, here goes...

Two drives:
hda - 200gb currently with XP
hdb - 160gb currently with 7.04

I'm very happy with the way 7.04 has turned out for me, and testing 7.10 has been successful, so it's time to wipe it all clean with a big, fat hose and start fresh.  I'd like to put 7.10 on hda when it's officially released, I will then use my hdb to place in my NAS enclosure and use it for network storage... but that's the easy part.

I've never set up my /home drive to reside on a separate partition.  So how can I go about doing this?  Is there a specific set of steps needed during the install?  I will backup my current /home folders.  Can I just copy the /home folder back onto the new install when done?  /etc is also mentioned as a good folder to backup.  Thoughts?

---

### Post by morleyrees on 2007-10-04
Hi,

I tend to keep my /home on a separate partition.  This makes clean installs easier in future.  Just remember to partition manually in the first instance **AND** in the future.  It gives you the option to do this when your installing.

I tend to partition as follows:-

/boot  approx 100MB
/         approx 10-20GB
swap double installed memory eg 1GB main memory=2GB swap

The rest for /home.

Obviously all this depends on the size of your hard drive in the first instance.  You will have to install a large number of apps to fill up 20GB of /

You should be able to copy your current /home over later.  Remember to try to preserve the owner and group info when copying.  Just take into account that the old personal settings for your apps will also be copied over.

You're correct, it is a good idea to back up /etc.  A lot of your system wide settings are under this directory.

HTH.

Mike

---

### Post by derekr44 on 2007-10-04
Thank you very much, Mike.  I found [this thread](http://ubuntuforums.org/showthread.php?t=46866) about telling Ubuntu where your /home partition resides, so I think I will try that out.  I plan on using the 200gb drive as hda.  My /home folder is already over 30gb due to Crossover installations and VirtualBox.  So my /home partition is going to be rather large.

I'm thinking the following:
/boot - 200MB
/ - 70GB
/swap - 4.8GB
/home - 125GB

---

### Post by maybeway36 on 2007-10-04
You probably don't need a seperate partition for /boot, but it's not going to really have any detrimental effects. That looks good the way you have it.

---

### Post by derekr44 on 2007-10-04
Speaking of which, what are the benefits/reasons to have or not to have a seperate partition for boot?  Is it mainly just to keep things organized or what?

---

### Post by elvis on 2007-10-04
> **derekr44 said:**
> Speaking of which, what are the benefits/reasons to have or not to have a seperate partition for boot?  Is it mainly just to keep things organized or what?

I like to have /boot separate.  For systems that need to be secured, you can manke /boot read-only (or go one step further and have it be unmounted after the boot process has cmopleted).  This ensures nobody can write information to the /boot partition while the system is running, making things a bit more secure.

Secondly, if your system shuts down incorrectly (power outage, etc) having a separate boot partition (especially if you use the unmount-after-boot option above) means there's less chance it needs to have fsck run on next boot.

Thirdly, for some older hardware, they must have the boot image / kernel in the first 512MB or 2GB from the beginning of the disk.  A /boot partition will ensure this always happens.

My average system setup is as follows (and created in this order)

/boot - 100-200MB (depending if I have custom recovery images in there like Memtest and [INSERT Rescue CD]("http://www.inside-security.de/insert_en.html").

Swap - depends on the system's need.  For desktops I typically match the installed RAM size.  For servers it depends on what they do and how much local memory there is.  No hard and fast rules here.

/ - 10GB.  I keep this small for reasons I'll explain in a bit...

/home and any custom mount points (/data , /mysql , etc) are stored on [Linux LVM]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)").  This means I can resize them as needed.  Additionally, it means I can use LVM Snapshotting to back up entire partitions in a few seconds, and from there take my sweet time to copy/tar/backup the information to some other source (another machine, DVD-R, tape, etc).

I firmly believe that any variable data does not belong in the root path and subpaths.  I think default locations for software like mysql and named (inside /var/lib) are just silly.  I'll either symlink them back to my custom mount points, or change config files so that the programs always look to the correct place. This makes backing up machines a piece of cake, because I don't need to go hunting for all the bits and pieces.  As long as I have /etc, /home and my custom LVM points backed up, I know my data is safe.

---

### Post by derekr44 on 2007-10-04
This is really interesting.

So with Linux LVM, can you pretty much (not that you'd really want to) set a separate partition for any "folder", such as /etc or /usr?  And you can dynamically control the size of the partition?

I guess it's time for me to read up on fstab and partition editing.  I haven't played with custom partitions since the days of Windows 98...

---

### Post by derekr44 on 2007-10-04
Here's a thought...

I just [read](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive) that placing /home on a completely separate drive yields performance benefits because of IO, is easier to backup and allows me to use just the one drive to swap around to just about any Linux machine with minimal effort.

Should I use the 200GB drive as /home instead?

That way I could do:

hda
/boot - 200MB
/ - 155GB
/swap - 4.8GB

hdb
/home - 200GB

---

### Post by liegerm on 2007-10-05
> **derekr44 said:**
> 
I've never set up my /home drive to reside on a separate partition.  So how can I go about doing this?  Is there a specific set of steps needed during the install?  I will backup my current /home folders.  Can I just copy the /home folder back onto the new install when done?  /etc is also mentioned as a good folder to backup.  Thoughts?

There's a couple of ways of doing this: 1. during installation, 2. by editing fstab and moving you data. Number 1 is preferable.

Both methods are described quite well elsewhere -- just Google them or have a look here: [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing).

Hope this helps.

---

### Post by elvis on 2007-10-05
> **derekr44 said:**
> Should I use the 200GB drive as /home instead?

That way I could do:

hda
/boot - 200MB
/ - 155GB
/swap - 4.8GB

hdb
/home - 200GB

That's how I would do it in your situation, yes.

---

### Post by derekr44 on 2007-10-05
Ok, I did it!  It took a few hours, but now I have my /home residing on the 200GB drive as hdb1 with my fresh Ubuntu installation sitting on the 160GB hda.  Thanks for all the help guys, I can tell a difference already!

---

### Post by derekr44 on 2007-10-05
Another odd one.

Now I've got a completely fresh install.  I've got an nVidia 7600GT and have successfully installed the newest nVidia restricted drivers.  My monitor is a 19" widescreen LCD that runs at 1440x900.

After installing the restricted drivers, I am prompted to reboot... which I do.  After rebooting, the GRUB menu is displayed, I select my flavor and I see the "Starting Up..." text.  Then it disappears and my monitor hibernates.  The computer is still running as normal because I can hear the login sounds through the speakers.

So I hit Ctrl+Alt+F1 to bring up the CLI and log in.  I sudo to check my /etc/X11/xorg.conf file and see that nvidia is selected as the driver, ALGX is set to True and my modes list "1440x900", "1024x768" and "800x600".

The ONLY way I can get my resolution set straight is to enable Twinview, plug my 17" CRT in the other video port on the card, log in, change my resolution in the GUI to 1440x900 and disable the CRT in the Twinview settings in nvidia-settings.

Does this sound like a little much?  I don't see why I should have to enable Twinview and use a second monitor to force my preferred resolution.

---

