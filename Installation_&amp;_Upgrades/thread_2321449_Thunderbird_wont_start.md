---
title: "Thunderbird wont start"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by expatver on 2016-04-22
Machine has 2 installations of 16 LTS.  This one is a new install on a new HD. The other is an upgrade from 14 LTS via the live Cd (not the apt path).  Both the ungrade and the new install are from the same CD.  On the upgraded install, Thunderbird starts and runs fine. On the new install Thunderbird attempts to start  and nothing.  sudo apt-get purged and reinstalled Thunderbird. Still nothing when trying to start from the program icon.  From terminal  the program will start  as sudo thunderbird.  The terminal yields this message 

------------------------------------------

sudo thunderbird
[sudo] password for "user": 


(process:18333): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

-------------------------------------------

any ideas about how to remedy this?  I found a similar problem elsewhere  that created this error because of another instance of thunderbird running in the background. I checked with htop  and  thats not whats happening here. 

I also asked this at the Thunderbird help forum with so far, no results. 

Any help or direction would be deeply appreciated.

Expat

---

### Post by kc1di on 2016-04-22
in a terminal just type thunderbird no sudo 
post any error messages it spits out.

---

### Post by expatver on 2016-04-22
Here is the output  sans sudo. Will not start except as sudo.

Thanks

------------------
(process:20725): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Could not create gnome accelerators directory `/home/carr/.gnome2/accels': Permission denied
---------------

Expat

---

### Post by kc1di on 2016-04-22
Go to a terminal and type this command and see if it will allow thunderbird to start.
```
sudo chmod 755 /home/carr/.gnome2/accels
```
hit enter, then enter your password then enter again.   There will be no output.

then try to start thunderbird again.  let me know if it works or not.

---

### Post by expatver on 2016-04-22
Thanks very much. Unfortunately no difference. Tried this both with Thunderbird running and  shut down. Tried starting from the GUI and nothing. 

This is still the output when trying to start from the CLI non sudo
--------------------------------------------------------
(process:887): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Could not create gnome accelerators directory `/home/carr/.gnome2/accels': Permission denied
--------------------------------------------------------
Expat

KF4VAR

---

### Post by kc1di on 2016-04-22
Hi KF4VAR Glad to meet you,

Which desktop are you using Unity?

---

### Post by expatver on 2016-04-22
Dave

Yes, Unity, Pretty much stock install here. On the other HD on this machine, the upgrade (and that was a bit of a hack due to a possible bug in the live CD upgrade path but thats another story) Thunderbird will start fine. Here no. 

Expat

Turning into crap.  Right after I installed this,  I installed Chromium. So I had no opportunity to try to start Firefox until a few minutes ago. From the GUI, same as Thunderbird, wont start. From the CLI this

---------------------------
firefox
Could not create gnome accelerators directory `/home/carr/.gnome2/accels': Permission denied
---------------------------

So I guess its everything Mozilla. I do know  with certainty that the upgraded install on the other drive runs not only Firefox but Thunderbird as well without hitch.

Update

Permissions-
```
sudo chown -R user:user /home/carr/.gnome2
[sudo] password for user:
```  

after this chown it eliminated the permissions problem on /home/carr/.gnome2/accels. Now, Firefox will start and run no problem.  When I attempt to start Thunderbird, I get the dreaded "already running. To start another instance, first kill the running window or reboot your system."  Using htop or ps, yields no running Thunderbird process. Not there. Likewise grepping  thunderbird 

```
sudo ps -a | grep thunderbird
```
 
nothing there. Rebooting yields again the dreaded  already running message.  Went to /home/thunderbird folder and did away with the parentlock  file. Looked for a lock file (where the program  shut down improperly and didnt release the locked profile. Not there.  Still will not start from the GUI or from CLI as /usr. When cli "thunderbird" the following result

```
(process:3336): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
```

and from Mozilla 

"This bug appears to have reemerged when firefox runs under glib 2.36"

We appear to be  on 2.48 from what I can tell here. 

Suggestions?

Thanks

---

### Post by kc1di on 2016-04-23
Hi Again, 
Try changing the owner of the```
 /home/<usr name>/.thunderbird
``` file.  You may also have to change permissions.
see if that works.

Alternatively you could copy the .thunderbird file from the working H.D. to the new install and see if that would work.  if you do rename the .thunderbird file on the new install to something else like .thunderbird-bak 
good luck ;)
73 , Dave

---

### Post by expatver on 2016-04-23
Hi Dave

Well-  Tried copying the .thunderbird file  per your suggestion. Dont ask me why but at that point the OS thought the program was no longer installed.  Fine. Installed Thunderbird. Managed to start it. Went through the setup wizard fine until the point where it wants to save the new profile file to .thunderbird.  It refused, saying  no permissions. chowned .thunderbird. Locked the icon to the launcher  and the thing actually started, I was amazed.  So far so good. 

What else I did do was to  download another 16 .iso and burn it to a DVD and again checked for data integrity. If it had not worked out as easily as it has so far I was going to  do  a re install.  I still dont know whether this has all been some sort of flaw in the new OS or a flaw in my install. Either way, another problem like this and nuke and pave time. 

73

Carr

Didnt say thanks in the last post- Many kind thanks for your excellent assistance in all of this.  It is deeply appreciated. Hope to catch  you on the air someday. I dont have any equipment here and miss operating. Part of the reason I am thinking about moving back to the US. 

Again many thanks for your help and my pleasure to make your acquaintance. 

73

Carr

Guess we can call this resolved

---

### Post by kc1di on 2016-04-24
Your Welcome Carr, 
Hope we catch up on the air one day.  I'm not on much right now but who knows. 

please take a moment and mark the thread as  solved. 
73,
Dave

---

