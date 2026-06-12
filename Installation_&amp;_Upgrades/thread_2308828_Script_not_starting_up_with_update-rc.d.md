---
title: "Script not starting up with update-rc.d"
date: 2016-01-06
forum: Installation &amp; Upgrades
---

### Post by lendon210 on 2016-01-06
Hi I am trying to configure a headless Ubuntu 14.04.3 server with kernel 3.19.0-43-generic to startup qbittorrent-nox automatically. I am following this [tutorial]("https://github.com/qbittorrent/qBittorrent/wiki/Running-qBittorrent-without-X-server") and for some reason the service is never started and I cannot connect to it using my browser. If I were to start the service manually it would work fine though.

I have also followed the instruction of the script made by Jesper Smith and changed the USER= portion to reflect my own user account. I have already confirmed my system init is using init.d through the command "sudo stat /proc/1/exe". At this point I am stump on how to get this working. Please any help to resolve this issue would greatly be appreciated!

---

### Post by ian-weisser on 2016-01-06
How did you confirm that the service is not started?

---

### Post by lendon210 on 2016-01-06
Through checking it on my browser and using the "service qbittorrent-nox status" status.

---

### Post by ian-weisser on 2016-01-06
Any relevant errors in /var/log/syslog?
Did you get any mysterious errors while following the tutorial?
You are certain you followed every step of the tutorial, in order?

---

### Post by lendon210 on 2016-01-06
Nope there are no errors in /var/log/syslog
I have followed the tutorial exactly as it is. Not sure why the script would not execute at boot.

---

### Post by matt_symes on 2016-01-07
Hi

Can we check your system.

Please post the output of these commands.

```
dpkg -l qbittorrent-nox
```

That's a small L above.

```
ls -l /usr/bin/qbittorrent-nox
```

```
ls -l /etc/init.d/qbittorrent-nox-daemon
```

```
ls -l /etc/rc?.d/*qbittorrent-nox-daemon*
```

That'll just verify the basics.

Did you compile from source, install from the repositories or install from the PPA ?

Kind regards

---

### Post by lendon210 on 2016-01-07
Sure thing Matt, thanks for helping.

The code ```
dpkg -l qbittorrent-nox
``` yields:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                Version                                 Architecture Description
+++-===================================-=======================================-============-===============================================================================
ii  qbittorrent-nox                     3.3.x~6312-20151029~trusty1             amd64        bittorrent client based on libtorrent-rasterbar (without X support)
```

The code ```
ls -l /usr/bin/qbittorrent-nox
``` yields:
```
-rwxr-xr-x 1 root root 3367904 Oct 28 16:45 /usr/bin/qbittorrent-nox

```

The code ```
ls -l /etc/init.d/qbittorrent-nox-daemon
``` yields:
```
-rwxrwxr-x 1 root root 2535 Jan  5 23:05 /etc/init.d/qbittorrent-nox-daemon

```

And the code ```
ls -l /etc/rc?.d/qbittorrent-nox-daemon
``` yields:
```
lrwxrwxrwx 1 root root 32 Jan  6 22:50 /etc/rc0.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon

```

I have installed it through the official ppa (**ppa:qbittorrent-team/qbittorrent-stable) **as they provides the more updated version than the Ubunutu server.

---

### Post by matt_symes on 2016-01-07
Hi

> **lendon210 said:**
> 
And the code ```
ls -l /etc/rc?.d/qbittorrent-nox-daemon
``` yields:
```
lrwxrwxrwx 1 root root 32 Jan  6 22:50 /etc/rc0.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon

```


That's your problem there. The script is only being run at runlevel 0; at poweroff.

However, I've just had a good look at the web page you linked to in post #1 and noticed this..

> Warning! Ubuntu 15.04 switched to Systemd, do not use the script below with 15.04, it will be corrected.  

You say you're on 14.04.3 so this should not apply to you.

You ran this correctly ?

```
sudo update-rc.d qbittorrent-nox-daemon defaults
```

Kind regards

---

### Post by lendon210 on 2016-01-07
Yes I did ran that command correctly.

---

### Post by matt_symes on 2016-01-07
Hi

> **lendon210 said:**
> Yes I did ran that command correctly.

Then something went wrong as according to the init.d script, it should have created the symlinks...

```
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
```

and it only created *Default-Stop:      0*.

Can you run these commands again and post all the output from the terminal (including the commands themselves for context)

```

sudo update-rc.d qbittorrent-nox-daemon remove
sudo update-rc.d qbittorrent-nox-daemon defaults
ls -l /etc/rc?.d/*qbittorrent-nox-daemon*
```

If it does not work then we can try enabling each runlevel manually and see what happens.

Kind regards

---

### Post by lendon210 on 2016-01-07
Here are the outputs:

```
sudo update-rc.d qbittorrent-nox-daemon remove
Removing any system startup links for /etc/init.d/qbittorrent-nox-daemon ...
   /etc/rc0.d/K20qbittorrent-nox-daemon
   /etc/rc1.d/K20qbittorrent-nox-daemon
   /etc/rc2.d/S20qbittorrent-nox-daemon
   /etc/rc3.d/S20qbittorrent-nox-daemon
   /etc/rc4.d/S20qbittorrent-nox-daemon
   /etc/rc5.d/S20qbittorrent-nox-daemon
   /etc/rc6.d/K20qbittorrent-nox-daemon

```

```
sudo update-rc.d qbittorrent-nox-daemon defaults
 Adding system startup for /etc/init.d/qbittorrent-nox-daemon ...
   /etc/rc0.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc1.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc6.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc2.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc3.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc4.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc5.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon

```
For the "ls -l /etc/rc?.d/qbittorrent-nox-daemon" command it says "Cannot access /etc/rc?.d/qbittorrent-nox-daemon: No such file or directory"

However, if I check the folders within /etc/rc0.d/ through /etc/rc5.d/ I do see a file with K20 or S20 followed by bittorrent-nox-daemon.

---

### Post by matt_symes on 2016-01-07
Hi

> **lendon210 said:**
> Here are the outputs:

```
sudo update-rc.d qbittorrent-nox-daemon remove
Removing any system startup links for /etc/init.d/qbittorrent-nox-daemon ...
   /etc/rc0.d/K20qbittorrent-nox-daemon
   /etc/rc1.d/K20qbittorrent-nox-daemon
   /etc/rc2.d/S20qbittorrent-nox-daemon
   /etc/rc3.d/S20qbittorrent-nox-daemon
   /etc/rc4.d/S20qbittorrent-nox-daemon
   /etc/rc5.d/S20qbittorrent-nox-daemon
   /etc/rc6.d/K20qbittorrent-nox-daemon

```

```
sudo update-rc.d qbittorrent-nox-daemon defaults
 Adding system startup for /etc/init.d/qbittorrent-nox-daemon ...
   /etc/rc0.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc1.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc6.d/K20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc2.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc3.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc4.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon
   /etc/rc5.d/S20qbittorrent-nox-daemon -> ../init.d/qbittorrent-nox-daemon

```


That looks really good.

> For the "ls -l /etc/rc?.d/qbittorrent-nox-daemon" command it says "Cannot access /etc/rc?.d/qbittorrent-nox-daemon: No such file or directory"

Sorry. That's a typo in my original command that i copied and pasted a second time. It should have been

```
ls -l /etc/rc?.d/*qbittorrent-nox-daemon*
```

I've had a very long, tough week so far and it's not getting much better. It may point to my post #8 as being an incorrect diagnosis. Once again, sorry.

I'll edit my previous posts to remove the typo.

> However, if I check the folders within /etc/rc0.d/ through /etc/rc5.d/ I do see a file with K20 or S20 followed by bittorrent-nox-daemon.

Try rebooting. It should now start. 

If it doesn't then something else is wrong and we should check its configuration next.

Kind regards

---

### Post by lendon210 on 2016-01-07
We all have those long tough weeks. Thanks for putting in the time and effort to helping me resolve this issue, I really appreciate your continued assistance.

Well I just did a "sudo reboot" and tried to access qbittorrent through the browser and it would not load up. However, if I did "sudo service qbittorrent-nox-daemon" start" the qbittorrent would load up and I could access it through the browser.

---

### Post by matt_symes on 2016-01-07
Hi

I've just had a good look through the file qbittorrent and saw this

```

# Description:       Start qbittorrent-nox on start. **Change USER= before running**
```

and further down this

```
USER=[USERNAME]
```

I think we need to set USER to a valid username. It is saying that.

So we can see what user qbittorrent is starting under when you start it manually, please post the output of this command.

```
ps aux | grep qbittorrent
```

Can you also post the output of...

```
whoami
```

...as it would be better to run it under your username.

That may get us closer and the script does suggest it needs to be changed.

Kind regards

---

### Post by lendon210 on 2016-01-07
Yes I have read and changed that portion to reflect upon my own username. I have changed it to USER="central" and USER=central. Both of which works when I run the "sudo service qbittorrent-nox-daemon start" command but fails to startup the scripts upon boot. USER=["central"] and USER=[central] both gives errors.

Here are the outputs you have requested:
```
ps aux | grep qbittorrent
central   1394  0.4  1.2 361304 12376 ?        Sl   13:23   0:00 /usr/bin/qbittorrent-nox
central   1449  0.0  0.2  11748  2260 tty1     S+   13:24   0:00 grep --color=auto qbittorrent
```

```
whoami
central
```

---

### Post by matt_symes on 2016-01-07
Hi

> **lendon210 said:**
> Yes I have read and changed that portion to reflect upon my own username. I have changed it to USER="central" and USER=central. Both of which works when I run the "sudo service qbittorrent-nox-daemon start" command but fails to startup the scripts upon boot.


That's just plain odd. I may be due to ordering perhaps....

> USER=["central"] and USER=[central] both gives errors.

That's what i would expect. What you did previously was correct.

I am going to download Ubuntu 14.04.3 server now, spin up a VM and install qbitorrent and see how i get on because I'm rather stumped at the moment and i want to see what happens when i try it.

I post back when i have done that.

Kind regards

---

### Post by lendon210 on 2016-01-07
Thank you so much for investigating this! Hopefully you will be able to find out what the problem is. On a second note, it seems as though the version of the kernel does not matter. I have tried it on a server with 3.19.0-43-generic and on a virtual server with 3.19.0-25-generic (default kernel shipped with Ubuntu server 14.04.3) and on both kernels the qbittorrent does not start on boot.

---

### Post by matt_symes on 2016-01-07
Hi

> **lendon210 said:**
> Thank you so much for investigating this! Hopefully you will be able to find out what the problem is. On a second note, it seems as though the version of the kernel does not matter. I have tried it on a server with 3.19.0-43-generic and on a virtual server with 3.19.0-25-generic (default kernel shipped with Ubuntu server 14.04.3) and on both kernels the qbittorrent does not start on boot.

You're not going to like this but i followed the instructions on that page and it works on my VM.

1. I installed 14.04.3 and reboot.
2. sudo apt-get update/upgrade and reboot.
3. sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable
4. sudo apt-get update
5. apt-cache policy qbittorrent-nox => to check it would install frm the PPA and not the repo.
6. sudo apt-get install qbittorrent-nox
7. sudo wget -O /etc/init.d/qbittorrent-nox-daemon [http://launchpadlibrarian.net/38905385/qbittorrent](http://launchpadlibrarian.net/38905385/qbittorrent)
8. sudo nano /etc/init.d/qbittorrent-nox-daemon => USER=matthew
9. sudo chmod 755 /etc/init.d/qbittorrent-nox-daemon
10. sudo update-rc.d qbittorrent-nox-daemon defaults
11. sudo reboot
12. ps aux | grep qbittorrent => To check it's running (/usr/bin/qbittorrent-nox)
13. sudo apt-get install links2
14. links2 http://<server_ip>:8080 => To check to can get to the admin page from the server. I set up as NAT and not bridged.

I'm not really sure what to suggest but you may want to spin up a VM and try to install it like i just did.

**EDIT:**

Works in bridged mode as well.

I'll have a think about why it may not be working for you but you may want to experiment in a VM.

Kind regards

---

### Post by lendon210 on 2016-01-07
Hey Matt, thank you so much for going through all this trouble.

So I think I may have found the culprit. Before I go into the details, could I ask you if you had selected to have your home directory encrypted at the installation?

After seeing how you got it to work, I thought maybe it could be a setting in the Ubuntu Server installation that is messing this up.

What I did was I did a fresh server install on vbox and selected all the settings I would like (encrypt home directory, OpenSSH server, samba file server) and went through all your steps. End result was qBittorrent would not load up on boot.

Then I went ahead and did a fresh server install on vbox, **but this time I didn't check encrypt home directory** but kept all the other settings (OpenSSH server and samba file server) and went through all your steps. The end result was that the qBittorrent loaded up at boot! I could even access it through my browser. I can't believe it was the home folder encrypt that would be causing this.

Since my server has its home directory encrypted, how would I solve this problem? Is it a security or permission issue?

Thanks Matt!

---

### Post by matt_symes on 2016-01-08
Hi

> **lendon210 said:**
> Hey Matt, thank you so much for going through all this trouble.

So I think I may have found the culprit. Before I go into the details, could I ask you if you had selected to have your home directory encrypted at the installation?

After seeing how you got it to work, I thought maybe it could be a setting in the Ubuntu Server installation that is messing this up.

What I did was I did a fresh server install on vbox and selected all the settings I would like (encrypt home directory, OpenSSH server, samba file server) and went through all your steps. End result was qBittorrent would not load up on boot.

Then I went ahead and did a fresh server install on vbox, **but this time I didn't check encrypt home directory** but kept all the other settings (OpenSSH server and samba file server) and went through all your steps. The end result was that the qBittorrent loaded up at boot! I could even access it through my browser. I can't believe it was the home folder encrypt that would be causing this.

Since my server has its home directory encrypted, how would I solve this problem? Is it a security or permission issue?

Thanks Matt!

My home partition was not encrypted :)

Very good sleuthing. That'll be the problem and I'll place money on it.

Try full disc encryption (LUKS/dm-crypt) if you are using home partition encryption.

I'll run a test tonight here.

Kind regards

---

### Post by lendon210 on 2016-01-08
Thanks Matt.

Would it be possible to make it work under the current conditions or would I have to go with full disc encryption? I tried creating a new user with sudo privileges and running the same installation but qBittorrent failed to start at boot on the main central user.

---

### Post by matt_symes on 2016-01-08
Hi

> **lendon210 said:**
> Thanks Matt.

Would it be possible to make it work under the current conditions or would I have to go with full disc encryption? I tried creating a new user with sudo privileges and running the same installation but qBittorrent failed to start at boot on the main central user.

I'll have a play tonight and see if i can come up with anything.

Firstly, it really does depends if qbittorrent is definitely not starting due to the encryption and, if it is due to encryption, there may be a work around if qbittorrent is started after the home partition is unencrypted.

As i said though, i can't look it until tonight (at some point - it may be late) and that's UK time.

Kind regards

---

### Post by lendon210 on 2016-01-08
Thanks for all you've done Matt.

---

### Post by matt_symes on 2016-01-09
Hi

*I'm going to edit this post as i have a play so keep checking out this post*

*I've finished editing this post now.*

I can confirm that it does not start with home partition encryption.

It **does** works if using full disc LUKS/dm-crypt encryption as expected.

What i think may be happening is qbittorrent is trying to access the home partition in some way while it's encrypted. 

The problem is that it's not unencrypted until you log in at the console. That is why you can start qbittorrent as a service after you have logged in because, at that point, the home partition is unencrypted.

There may not be a way around this (you may have to unencrypt your home partition before qbittorrent will start) but I'll run some more tests to confirm that this is what qbittorrent is doing.

*********

Precondition:

qbittorrent is configured to run as user matthew in the file /etc/init.d/qbittorrent-nox-daemon

Test:

1. Booted up the VM that has the encrypted home partition for the user 'matthew'. 
2. Logged in a user matthew. 
3. Added another user, after picking a name at random, called 'harry' and added harry to the sudo group. 
4. Logged out of user matthew and logged into user harry and tried to start the qbittorrent service.
5. The qbittorrent service did not start, presumably because user matthew's home partition is encrypted at this point.

********

Right. I know what the problem is, i think.

When you boot up and before you log in to your encrypted home directory, your home directory is, obviously, encrypted.

But more than that, these are permissions of your home directory shown below.

(These are mine as an example. Yours will be the similar if you check. The *?* below are place holders for unimportant information.)

```
**dr[COLOR="#0000FF"]-[/COLOR]x------** ? matthew matthew ? ? ? ? matthew
```

Notice that you cannot write to the directory (in blue) as it has no 'w' flag.
When you login your home directory is set to writable and unencrypted. I think the sub-directories may also be non writable until they are unencrypted. This would be consistent behaviour.

Creating a wrapper script for /usr/bin/qbittorrent-nox so it's straced to a file in /tmp, shows that  qbittorrent-nox tries to create a new directory in a sub-directory of your home directory. 

This sub-directory is your .local directory (in my case /home/matthew/.local) but as your encrypted directories are not writable, qbittorrent-nox can't create the new directory and exits.

This is why qbittorrent cannot start if you have an encrypted home directory until you have logged in.

So in conclusion, qbittorrent is getting a permission denied error and failing when trying to create a directory in $USER/.local. It's then exiting. I *think* this may be due to the permissions on the home directory and sub directories, as i suspect but have not checked, the sub directories under your home directory are also not writable.

There's no way around this with *seriously* weakening your encryption so you really, really don't want to attempt to change this behaviour. Otherwise what's the point of encryption.

So you have two realistic options.

1. Use no encryption at all.
2. Use LUKS/dm-crypt for full disc encryption.

Kind regards

---

### Post by lendon210 on 2016-01-09
Excellent work detective Matt! While it is unfortunate to not find a work around for this situation, I guess I had to deploy another workaround to this. 

What I did was upon boot login to my central account
 start up qbittorrent-nox
press ctrl+z to halt the qbittorrent process
then type in bg to send the process into the background

This has worked for me so far even after I logged out of my account. Obviously qbittorrent will not automatically run after reboot but it is not too often do I need to restart the server.

I have looked into the LUKS/dm-crypt you suggested and it seems as though they require a full system backup before proceeding. With my Pentium 4 old computer, that would take days to move data onto a different storage, reformat, and then transfer it back to the machine.

Thus, I am just going to remove the home encryption all together.

In conclusion, thank you so much for sinking countless hours into helping me with this problem, Matt :D. I truly appreciate your very informative and detailed posts you've written in assisting me. If you have a better method please don't hesitate to share it with me.

---

### Post by matt_symes on 2016-01-10
Hi
> 
I have looked into the LUKS/dm-crypt you suggested and it seems as though they require a full system backup before proceeding. With my Pentium 4 old computer, that would take days to move data onto a different storage, reformat, and then transfer it back to the machine.

A Pentium 4 may really struggle with full disc encryption because it does not have the CPU AES instructions that more modern CPU's have build into them.

With these instructions built in, AES encryption/unencryption can be performed natively by the CPU and is *much* quicker to do than CPUs without the native instructions. A Pentium 4 is an older chip as well..

AES is pretty much the symmetric encryption standard you want to be using as well these days.

If i was in your situation, i would probably go down the "no encryption" route if upgrading the server is not an option.

Another option maybe to download the files to an unencrypted user and, when downloaded, copy them to an encrypted filing system. The copy could be done at low priority and, when  the copy is complete and has been verified using maybe an MD5 hash of both file to ensure they are the same, **shred** could be run on the old file to securely removed it (as securely as you can do these days). This is a bit clunky solution but it should work. It can all be scripted and can use existing tools such as inotifywait. I would need to ponder the fecundity of this idea though.

> 
In conclusion, thank you so much for sinking countless hours into helping me with this problem, Matt . I truly appreciate your very informative and detailed posts you've written in assisting me. If you have a better method please don't hesitate to share it with me.

It's my pleasure :).

Kind regards

---

### Post by lendon210 on 2016-01-10
Yep I agree with you on the Pentium 4 struggling with the AES encryption. At a minimum I think maybe be a Core 2 Duo should be used in order to ensure smooth operation.

---

