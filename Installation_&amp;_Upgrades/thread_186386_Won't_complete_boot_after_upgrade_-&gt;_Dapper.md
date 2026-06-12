---
title: "Won't complete boot after upgrade -&gt; Dapper"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by carlos1 on 2006-06-01
On my notebook (Acer TravelMate 8100) I was running Breezy just fine, and today updated to Dapper with apt-get update and apt-get dist-upgrade.

When I rebooted, I got the new boot screen for Dapper (I assume, it looks different), which got all the way through, then when it finished, went to console briefly (too fast to see what it said) then went back to the boot screen, said it was running a couple of more processes, but stcuk after the second ("starting timidity" I think).  

Then it just hangs. 

During the upgrade, I could not install "kubuntu-default-settings" because it depended on "kwin-style-crystal" which would not install.  I'm not sure if this is the problem, or: 

Could it be that it's running something unnecessary in the boot script? It seems like it's running a whole second script, then getting stuck. 

Could someone point me to the file that gives the sequence of commands for booting, ie. which scripts are run, so I can possibly remove the offending lines? 

Many thanks.

---

### Post by catlett on 2006-06-01
Sorry I don't know the scripts but since you say you are going to remove then I assume you can get into your install? If you can get in to remove scripts try running ```
sudo aptitude dist-upgrade
```. Aptitude will try and solve the dependency issue. Hopefully it will and then will finish updating your install and everything works (hopefully)

---

### Post by dsh200 on 2006-06-01
I had a similar problem when upgrading a few minutes ago. I never saw what process it was dying on since it stayed in the boot screen.  I fixed it by launching into GRUB at the boot and selecting "Recovery Mode".  It then booted to the command line and I ran *sudo apt-get -f instal*l.  When the install finished it listed three errors:

Errors were encountered while processing:
postfix
mailx
mysql-server-4.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

I then did *shutdown -r now* to reboot and it came up fine.  I'm a linux newbie so I don't know if this will help or not but your symptons sounded just like mine.

---

### Post by carlos1 on 2006-06-01
Thanks I tried both of these but no joy on either.

I did try "startx" from recovery mode, and got two errors: 
couldn't find package "fglrx"
and 
couldn't find package "GLcore"

This is from /etc/X11/xorg.conf.

I tried to go in and change "fglrx" to "vesa" but every time I exited the document remained unchanged. 

grrr....

Does anyone know the name of the package specifically to install for the vesa drivers? 

Also is there another command to edit xorg.conf that would work?

---

