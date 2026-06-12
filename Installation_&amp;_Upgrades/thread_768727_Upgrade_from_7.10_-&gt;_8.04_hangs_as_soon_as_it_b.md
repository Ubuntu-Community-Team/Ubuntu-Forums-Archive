---
title: "Upgrade from 7.10 -&gt; 8.04 hangs as soon as it begins"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by a10waveracer on 2008-04-26
I'm currently running Ubuntu 7.10 on my Lenovo T61.  Whenever I attempt to run an upgrade from either the alternate CD or from the Update Manager, I get the following:

[IMG]http://www.thetacticalnuke.com/files/Screenshot.png[/IMG]

It does not matter which way I attempt doing it--if I go through the update manager it will give me the 'update notes', download the two files, use gksu to prompt me for admin privileges and then it stalls.  If I hit the 'update' button from the autorun off of the cd (or, alternatively, try "sh /cdrom/cdromupgrade") it asks me for admin and then gives that same picture again.  I left it running for 8 hours last night in the vain hope that it would work.... but it didn't.  Any prospective help would be awesome.

---

### Post by a10waveracer on 2008-04-26
Slight bump, but here's the image it will sometimes show when it first starts up "Distribution Upgrade"

[IMG]http://www.thetacticalnuke.com/files/Screenshot2.png[/IMG]

After that, however, it just hangs on me... and that's getting old.  Any ideas?

---

### Post by dresen on 2008-04-26
I was just about to make the same thread before i saw this, I am having the same issue, the upgrade manager will freeze up and never recover, here is a screenshot:
[img]http://uploader.ws/upload/200804/Screenshot1_1.png[/img]

---

### Post by a10waveracer on 2008-04-26
Dresen, could you do me a favor with the following two things:
First of all, could you check and see whether you are using the "US" or the "Main" server for apt?  You can figure it out in System->Administration->Software Sources.
Secondly, drop into terminal and "cd /etc/apt/sources.list.d" and tell me what, if anything, is in that folder.  I have a theory I want to test... Thanks.

---

### Post by dresen on 2008-04-26
> **a10waveracer said:**
> Dresen, could you do me a favor with the following two things:
First of all, could you check and see whether you are using the "US" or the "Main" server for apt?  You can figure it out in System->Administration->Software Sources.
Secondly, drop into terminal and "cd /etc/apt/sources.list.d" and tell me what, if anything, is in that folder.  I have a theory I want to test... Thanks.

I'm using the Main server and my sources.list.d folder is empty

---

### Post by a10waveracer on 2008-04-26
> **dresen said:**
> I'm using the Main server and my sources.list.d folder is empty

Well... that shoots down my theory.  I'm using US and have things in that folder.  Have you tried the alternate cd route?

---

### Post by dresen on 2008-04-26
> **a10waveracer said:**
> Well... that shoots down my theory.  I'm using US and have things in that folder.  Have you tried the alternate cd route?

not yet, but that's the plan

---

### Post by mathenge on 2008-04-26
> **a10waveracer said:**
> I'm currently running Ubuntu 7.10 on my Lenovo T61.  Whenever I attempt to run an upgrade from either the alternate CD or from the Update Manager, I get the following:

[IMG]http://www.thetacticalnuke.com/files/Screenshot.png[/IMG]

It does not matter which way I attempt doing it--if I go through the update manager it will give me the 'update notes', download the two files, use gksu to prompt me for admin privileges and then it stalls.  If I hit the 'update' button from the autorun off of the cd (or, alternatively, try "sh /cdrom/cdromupgrade") it asks me for admin and then gives that same picture again.  I left it running for 8 hours last night in the vain hope that it would work.... but it didn't.  Any prospective help would be awesome.

A lot of people have been having this problem. It's HUGE with this upgrade. I had the same problem all day Friday (April 25th). Most people thought it was due to servers being too busy, but I checked by manually using FTP or HTTP to connect, and was able to copy files.

In any case, I was able to work around that particular problem with a hack. I saw a post so please follow with utmost discretion. Here goes.

In my case, when the "Distribution Upgrade" dialog froze, I had to manually kill it. I did this by checking the running processes. In my instance, running the command:
        ps aux | grep python
revealed a process that looked something like:
        /usr/bin/pygthon /tmp/tmpXgyyZ/hardy
So I killed that process and the dialog went away.

Checking /etc/apt, I discovered that my sources.list file had already been converted to hardy sources so my update manager was going nuts and informing me that I had over 500 updates pending. Fortunately, I had a backup of /etc/apt/sources.list and copied that to restore sanity.

Anyway, once restoring sources.list, I ran the following command:

sudo /usr/bin/python /tmp/tmpXgyyZ/hardy --frontend=DistUpgradeViewText --mode=desk

(all on one line)

This will fire up the installation, in text mode.

In my case, the upgrade completed and I was able to login to Hardy. My main problems after that were mostly Video related (nvidia card), wireless NIC confusion as well as driver clashes.

---

### Post by a10waveracer on 2008-04-26
Well, that didn't work, but maybe now we're getting somewhere.  This is the error I now get:
> 2008-04-26 17:19:58,939 INFO release-upgrader version '0.87.24' started
2008-04-26 17:19:58,940 DEBUG Using 'DistUpgradeViewText' view
2008-04-26 17:19:58,996 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmp.nbIPCS7684/hardy", line 59, in <module>
    app = DistUpgradeController(view, options)

  File "/tmp/tmp.nbIPCS7684/DistUpgradeController.py", line 145, in __init__
    self.sources_backup_ext = "."+self.config.get("Files","BackupExt")

  File "ConfigParser.py", line 511, in get
    raise NoSectionError(section)

NoSectionError: No section: 'Files'


---

### Post by Tilos on 2008-04-26
I've attached an image of how far I get using the graphical update manager and the output from running apt-get clean, apt-get update and apt-get dist-upgrade.

---

### Post by a10waveracer on 2008-04-26
Just for kicks, here is the code when the graphical interface is used

> 2008-04-26 17:27:04,781 INFO release-upgrader version '0.87.24' started
2008-04-26 17:27:05,164 DEBUG Using 'DistUpgradeViewGtk' view
2008-04-26 17:27:05,210 DEBUG enable dpkg --force-overwrite
2008-04-26 17:27:05,276 DEBUG lsb-release: 'gutsy'
2008-04-26 17:27:05,276 DEBUG _pythonSymlinkCheck run

From there it just hangs.

---

### Post by a10waveracer on 2008-04-26
Giving this a bump for a different crowd--anyone else having this problem?

---

### Post by a10waveracer on 2008-04-26
By doing some more searching, I found this post:

[http://ubuntuforums.org/showpost.php?p=4792137&postcount=16](http://ubuntuforums.org/showpost.php?p=4792137&postcount=16)

That seems to be doing it for me--I'll post back once it is finished.

---

### Post by ciAnd7 on 2008-04-29
I have same problem. I try to upgrade 7.10(ThinkPad R60) by 8.04 DVD. Distribution Upgrade hangs showing "Checking package manager" label under progress bar.

---

### Post by clayts450 on 2008-04-29
Yup, having the same freeze on my old ancient IBM T22. Unfortunately the DVD route is not possible for me as this old thing is so tired and ancient the Ultrabay drive hasn't worked for ages.

I guess I'll stick with 7.10 then ;)

---

### Post by ArielMT on 2008-04-30
Happens to me, too.  Hangs as soon as it starts on a Dell Inspiron 600m, but it worked flawlessly on a no-name white box.  Both systems were running fully updated Gutsy yesterday.

---

### Post by ArielMT on 2008-04-30
Now it's working with the text front-end, but not the GUI front-end.  The only thing I did different was use "sudo su -" to get a real root login.

---

### Post by jthirt on 2008-05-01
I experience a similar problem, and tried to start the upgrade from the terminal to see if any errors came up and here is what I get :

```
pierre@nubuntu:~$ gksu 'update-manager -d'
warning: could not initiate dbus
extracting '/tmp/tmpcbxGmC/hardy.tar.gz'
authenticate '/tmp/tmpcbxGmC/hardy.tar.gz' against '/tmp/tmpcbxGmC/hardy.tar.gz.gpg' 

```

Not sure if this is important or symptomatic. 

I booted on the live CD to check if the new version worked fine on that PC and it did. So I'm now frustrated. 

Anybody knows how to resolve this ?

---

### Post by Spekkio on 2008-05-01
I'm having a similar problem. My upgrade hangs while trying to set up a program called chillispot. I've stopped and retried twice now. I'm frustrated. Help?

EDIT 2 May 2008
I got it. I had to go into aptitude in command line and kill the installation of chillispot. Then I was forced to configure a number of libraries by hand (dpkg --configure) to get out of dependency hell.

But hey, it's working. And miraculously, sound is working on my laptop for the first time since I got rid of Vista. I'd tried everything to get it to work. So kudos on that, Ubuntu team. YouTube isn't any good without sound.

---

### Post by petermck on 2008-05-03
Same problem on a laptop (Toshiba Satellite M50). No problem on a vanilla PC.
I'm doing apt-get dist-upgrade as root now and it seems to be working though I won't know for about 10 hours.
It appears that before the GUI upgrade freezes it gets as far as writing a new /etc/apt/sources.list and saves the old so if you don't have the Hardy CD you may have to comment out the CD source line.

---

### Post by petermck on 2008-05-04
I can confirm that running apt-get dist-upgrade as root worked for me. There was a couple of glitches, I had to ctrl-c out of one hanged process, but everything seems OK.
What ever the problem is with the update manager it seems to be only affecting the GUI.

---

### Post by kevind2071 on 2008-05-08
I experienced the same problem when trying to update.  I tried to switch servers by going to **System > Administration > Software Sources** and changing servers to the main server.

Another post suggested the command sudo do-release-upgrade from Terminal and I got it to work.  I am not sure why it works, but I was able to get hardy installed

---

### Post by adleberg on 2008-05-08
I tried upgrading from the alt cd because my internet is painfully slow, it continues to tell me i need to download 500+mb of packages and then i get a similar freeze to the previous posts...how do i get it to upgrade from the CD only?

---

