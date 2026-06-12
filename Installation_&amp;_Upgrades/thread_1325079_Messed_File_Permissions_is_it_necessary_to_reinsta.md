---
title: "Messed File Permissions/ is it necessary to reinstall?"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by suniyo on 2009-11-13
I am going through the same problem. I ran sudo chmod 777 -R * in wrong directory (to make it worse the directory was root /). So I was unable to even login to ubuntu. It threw me back to login screen even when I am logged in. It also gave me a graphical popup message saying: Install error: the config details for GNOME power manager has not been installed correctly. Contact your computer Administrator. 
Afte logging in (without letting me actually login) it gave me the error: there is problem with the configuration server. /usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status 256
 
After a bit of research I did following:

in recovery mode root prompt I run following commands:

```
chmod 755 /etc/gconf/gconf.xml.system
chmod 777 /tmp
chmod 700 /home/my_user_id
chmod -R 700 /home/my_user_id
chmod 644 /home/my_user_id/.dmrc 
```After that I was atleast able to login to Gnome session with root user.
Now I tried to check user/group permissions but it gave me the error: can not open unknown error occured. Wired Network devices can not load at the boot and are not editable anymore, so obviously I am not able to connect to the internet. So I am not able to do important administrative tasks and Audio is also missing. Things like System Testing is also not working. Most things that involves some kind of special privileges are not working. I need some help as there are lot many softwares (including servers/websites) installed and I don't want to reinstall ubuntu (after taking lot of backup). 

Even more research and through recovery mode root I changed /etc/sudoers permission to 0440 and was able to use sudo command in terminal but still administrative services are out of control.

I even tried to create new user but system denies to open services. So One thing I can do is to create new sudo su super user using terminal and can login with that user and change permissions in current user. Can someone tell me how to create new super user sudo user su using command line, terminal. **[COLOR=Red]OR[/COLOR]**

Can I restore my file permissions to default (0755/0644/0440 etc) by ubuntu.

Links to solution of the problem are okey...

Is it really necessary or compulsory to reinstall as it can be a lot of work for me. A whole week of extra work. (I don't even have backups :(()

---

### Post by suniyo on 2009-11-13
I have updated few files manually and few applications started working but I have thousands of them installed so is there any other way I can do this?

---

### Post by drs305 on 2009-11-13
In most cases a user who has done what you have and doesn't want to reinstall spends a long time trying to fix the system ... and then finally reinstalls anyway.

I would recommend a reinstall but there are some things you can do to make it less painful, if your system allows you to.

Make a copy of the installed packages via Synaptic. File, Save Markings. Make sure you tick the "save full state" in the lower left corner, and also that you save this to a partition that will not be formatted. You can then import them on the new system via Synapatic's "read markings".

You can also make a copy of your /home folder. Since it contains many of your configuration settings, it will help setting up your new system to be similar to your old one. If you can, you can move your /home to a separate partition now and use it during the new install (identify it but do NOT format it). There are several links on how to make a separate home partition (again, if your system lets you).

If find it useful to also just make copies of the /etc and /boot folders just in case I want to retrieve a file from it later.

Best of luck with whatever you decide to do.

---

### Post by suniyo on 2009-11-13
> **drs305 said:**
> 

Make a copy of the installed packages via Synaptic. File, Save Markings. Make sure you tick the "save full state" in the lower left corner, and also that you save this to a partition that will not be formatted. You can then import them on the new system via Synapatic's "read markings".

I have recovered a lot many things but still there is a lot of mess. The most important thing is that still I am unable to access user/group thing and Synaptic also. So markings are not possible right now. Is there anyway I can set correct file permissions for atleast markings via Synaptic. I have a script that I found on ubuntuforums for dpkg permissions restore. Should I give it a try? I am attaching it here for your reference. 

Thanks, any other help would be appreciated.

---

### Post by gtstephenson on 2009-11-14
I have a really unusual knome terminal problem. I've upgraded to 9.10 but have quite a few issues. (Mostly around networking). But the knome terminal is messed up. 

The "P" key doesn't work. Even a new install won't fixit. Has to be some configuration file in my directory but I have no clue where the config files are.

Any ideas?

Tom S.

---

### Post by drs305 on 2009-11-14
> **suniyo said:**
> I have recovered a lot many things but still there is a lot of mess. The most important thing is that still I am unable to access user/group thing and Synaptic also. So markings are not possible right now. Is there anyway I can set correct file permissions for atleast markings via Synaptic. I have a script that I found on ubuntuforums for dpkg permissions restore. Should I give it a try? I am attaching it here for your reference. 

Thanks, any other help would be appreciated.

Unfortunately that script doesn't rename the system files you need to repair. 

What error message do you get when you try to run Synaptic? The Synaptic file itself has permissions of -rwxr-xr-w. To get that, you would run:
```
sudo chmod 755 /usr/sbin/synaptic
```

However, you may not be able to use sudo. In which case, you need to add yourself back to the admin group. You may be able to do so by booting to the recovery mode, selecting "Drop to root prompt" and then adding yourself to admin with the following. Substitute your username for [COLOR="DarkRed"]*username*[/COLOR]:
```
adduser [COLOR="DarkRed"]*username*[/COLOR] admin
```

---

### Post by suniyo on 2009-11-14
Okey I will give it  a try today. Thanks for all the help. Network thing is not working so accessing internet is not possible through ubuntu so on dual boot I am using windows right now but few websites are down and I am not liking it. :) 

Will try to update user, synaptic and network and will post the results here. Bye for now.

---

### Post by suniyo on 2009-11-15
applying all the commands as you mentioned still able to access nothing
markings are okey if I don't get them I know what softwares I have installed but DATA is not backed up. Windows drives are not mounting so can not copy data there. DVDs or USB drives are also no mounting. Is there any other way I can take backup of all the data I have. 

I tried to access ext3 files on harddrive using these: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) & [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) but none worked. Are there any other ways to achieve this. I atleast need a good backup everything else would be okey.

Also not able to access mysql on command line or via phpmyadmin so DBs are lost anyway. Can I recover them?

I have added user to admin but still not able to access sudo it says suid not defined or something like that. hell of a mess.

---

### Post by kendoori on 2009-11-15
> **drs305 said:**
> 
I would recommend a reinstall but there are some things you can do to make it less painful, if your system allows you to.
Make a copy of the installed packages via Synaptic. File, Save Markings. Make sure you tick the "save full state" in the lower left corner, and also that you save this to a partition that will not be formatted. You can then import them on the new system via Synapatic's "read markings".
You can also make a copy of your /home folder. Since it contains many of your configuration settings, it will help setting up your new system to be similar to your old one. If you can, you can move your /home to a separate partition now and use it during the new install (identify it but do NOT format it). There are several links on how to make a separate home partition (again, if your system lets you).

If find it useful to also just make copies of the /etc and /boot folders just in case I want to retrieve a file from it later.

drs305, I've started on this prep, but was going to try to do an upgrade first using the alternate CD to see if it works. I was going to clone the drive first to an external device just to be safe.

I worked on moving my \home to a new partition today (done), and just now did Synaptic save markings thing (save to a different partition). 

Assuming I don't upgrade, but install fresh, can you describe the steps I would take that would allow me to restore my current applications and settings? Only caveat for me, is that right now my machine is dual boot, and my XP NTFS partition is the one that's marked as "boot."

---

### Post by suniyo on 2009-11-15
> **kendoori said:**
> drs305, I've started on this prep, but was going to try to do an upgrade first using the alternate CD to see if it works. I was going to clone the drive first to an external device just to be safe.

I worked on moving my \home to a new partition today (done), and just now did Synaptic save markings thing (save to a different partition). 

Assuming I don't upgrade, but install fresh, can you describe the steps I would take that would allow me to restore my current applications and settings? Only caveat for me, is that right now my machine is dual boot, and my XP NTFS partition is the one that's marked as "boot."

**[COLOR=Red]Solved[/COLOR]** almost. Live CD helped me a lot. 

[HTML]sudo nautilus [/HTML]

It gives me all necessary permissions to change and backup copies to a windows drive. Easy 20GB Data copies in just 30 minutes at 9Mbps on SATA. Now will try to recover using live CD for one last time if I can or other wise reinstall is good. In my case synaptic doesn't even allow to save markings. SUDO not working so there is too much mess and I have made it even worse, but I have a back up now :D 

Changing file permissions with millions of files is not possible so best thing is to reinstall that I have realized lately. Thanks to everyone for all the help. Amen.

---

### Post by drs305 on 2009-11-16
> **kendoori said:**
> Assuming I don't upgrade, but install fresh, can you describe the steps I would take that would allow me to restore my current applications and settings? 

If you have already created a separate home partition and designate that partition as your /home partition in the new install you will retain lots of your settings, such as configuration settings for the panels, shortcuts, etc. 

You would not retain settings for which you normally have to use admin rights to change, such as wireless settings. You could make a copy of the /etc folder, which contains some "root" configuration files that you may be able to copy to the new system (do not try to replace the new /etc with the old /etc, however!).

If you have saved the Synaptic list via the Save Markings option, on the new system you would use the "Read markings" option in the same section of Synaptic, telling it to use the list you created and saved from your old system.

---

### Post by kendoori on 2009-11-16
So, I've created a separate home partition on 9.04 (sda4), and am ready to do a clean install of 9.10 that I would like to take advantage of this home partition. I've downloaded the alternate installer CD, I assume that I will boot from the CD, then select "Install," rather than other try LiveCD options. At what point in the install process would I be able to point to this "home" partition?

Also, should I be concerned that the install will screw up my existing GRUB settings, given that I'm dual booting with XP?

---

### Post by suniyo on 2009-12-19
So you have solved the problem it seems, there is no option during the installation to point it to the home folder, though there are settings to import data from windows my documents folder and user accounts.

---

### Post by hakimoerton on 2010-01-03
> **suniyo said:**
>  ... there is no option during the installation to point it to the home folder ... 


Having reinstalled 9.10 so many times, it is possible to recognise your home partition during the partitioning section if you choose 'manual' partitioning.

Psychocat's site gives comprehensive instructions at: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

All the best,
Hakim

---

### Post by suniyo on 2010-01-03
> **hakimoerton said:**
> Having reinstalled 9.10 so many times, it is possible to recognise your home partition during the partitioning section if you choose 'manual' partitioning.

Psychocat's site gives comprehensive instructions at: [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

All the best,
Hakim


Problem is already solved, so it is irrelevent now. reinstallled the app again.

---

### Post by jlovi on 2011-11-13
.

---

### Post by jlovi on 2011-11-13
No drs305, it _is_ possible to come back from this messy situation without reinstalling your system. You only need to install a new system elsewhere and restore the permissions from there.

Here is how I did.

I ran again the same kind on issue (some bug in a script I was writing) and solved it, but you may need to ask some expert's help, if you're not one. In any case, be very cautuous!

First, my situation was easier to solve because I had a dual boot system (ubuntu and my former fedora install). Anyway, running the OS from a CD/DVD, or an USB key should do the same thing.

MPOINT=/mount/ubuntu

First I mounted my file systems like this (don't forget to create the mount points): mount /dev/ubuntu/root $MPOINT mount /dev/ubuntu/home $MPOINT/home

Then I ran the following command (my issue was only in a few - critical - directories) to copy the permissions on from the running system to the messy one (in fact, in my case, I installed an ubuntu system in Virtual Box under fedora and got the permissions there):

```
find /etc /usr /bin -exec stat --format "chmod -h %a ${MPOINT}%n" {} \; > /tmp/restoreperms.sh
```And then I ran the restoreperms.sh script.

I was able again to boot on ubuntu.

The content of restoreperms.sh will be something like:

```
(...)
chmod -h 755 /mount/ubuntu//etc/ppp
chmod -h 755 /mount/ubuntu//etc/ppp/ipv6-up
chmod -h 2750 /mount/ubuntu//etc/ppp/peers
chmod -h 640 /mount/ubuntu//etc/ppp/peers/provider
chmod -h 755 /mount/ubuntu//etc/ppp/ipv6-up.d
chmod -h 777 /mount/ubuntu//etc/ppp/resolv.conf
(...)
```I didn't test it but it must work for owners and owner groups too. Something like:

```
find /etc /usr /bin -exec stat --format '[ ! -L {} ] && chown %U:%G ${MPOINT}%n' {} \; > /tmp/restoreperms.sh
```Result:

```
(...)
[ ! -L /mount/ubuntu//etc/obex-data-server/imaging_capabilities.xml ] && chown root:root /mount/ubuntu//etc/obex-data-server/imaging_capabilities.xml
[ ! -L /mount/ubuntu//etc/obex-data-server/capability.xml ] && chown root:root /mount/ubuntu//etc/obex-data-server/capability.xml
[ ! -L /mount/ubuntu//etc/ppp ] && chown root:dip /mount/ubuntu//etc/ppp
[ ! -L /mount/ubuntu//etc/ppp/ipv6-up ] && chown root:root /mount/ubuntu//etc/ppp/ipv6-up
[ ! -L /mount/ubuntu//etc/ppp/peers ] && chown root:dip /mount/ubuntu//etc/ppp/peers
[ ! -L /mount/ubuntu//etc/ppp/peers/provider ] && chown root:dip /mount/ubuntu//etc/ppp/peers/provider
[ ! -L /mount/ubuntu//etc/ppp/ipv6-up.d ] && chown root:root /mount/ubuntu//etc/ppp/ipv6-up.d
[ ! -L /mount/ubuntu//etc/ppp/resolv.conf ] && chown root:root /mount/ubuntu//etc/ppp/resolv.conf
(...)

```Of course, you have to take care here, that the UID and GID are the same on both systems, but for the system related users and groups, this shouldn't be an issue.

Rk:

An important thing for this is to keep an install disk synchronized with the version you are using, or at least work with the current ubuntu version (may work even with diffenrent version but better to keep all the chances on your side).

Now, I have this commands in a cronjob, running every day (could be weeks) in order to keep that information. It will make the solution easier next time but, of course, as I have this now, it will never happen again. Something like this:

```
    0 12 * * * /usr/bin/find / -exec /usr/bin/stat --format="[ ! -L {} ] && /bin/chmod %a %n" {} \; -exec /usr/bin/stat --format="/bin/chown -h %U:%G %n" {} \; |/bin/bzip2 -c > /tmp/restore_fileperms.$(/bin/date +%w).sh.bz2
```

---

### Post by oldos2er on 2011-11-13
Closed, please don't bump old threads.

---

