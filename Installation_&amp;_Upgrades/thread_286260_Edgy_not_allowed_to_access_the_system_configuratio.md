---
title: "Edgy: not allowed to access the system configuration"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by phansiizwe on 2006-10-27
In Dapper I could access System->Administration->Networking by typing in my user password.
After upgrading to Edgy I get an error window stating:

```
The configuration could not be loaded
You are not allowed to access the system configuration.
```

Is this a new security policy or should I set some rights somewhere?


The same issue occurs when I try to access:

System->Administration->Services
System->Administration->Shared Folders
System->Administration->Time and Date
System->Administration->Users and Groups

---

### Post by silhouette on 2006-10-29
I'm getting this error too. Sudo and other administrative things (e.g. Synaptic) work, though.

---

### Post by toMeloos on 2006-10-29
same here :( 

Haven't found a solution yet.

---

### Post by phansiizwe on 2006-10-29
Though this doesn't solve the core of the problem, I have found a solution:

In a terminal (or from your menu, it didn't appear in my menus for some reason) start:

```
alacarte
```

This is a very good menu-editor for Gnome.

In the left listbox, scroll down and select System->Administration.
Now at the right, select e.g. Networking, click the right mousebutton and from the popup-menu select: Properties.

Now add

```
gksu 
```

in front of the *Command:* e.g.:

```
gksu network-admin
```

Repeat this for the entries:

[LIST]
[*]Services
[*]hared Folders
[*]Time and Date
[*]Users and Groups
[/LIST]

Now everything should work as expected.

Reported as a bug: 
[https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/69029](https://launchpad.net/distros/ubuntu/+source/meta-gnome2/+bug/69029)

---

### Post by Pawel on 2006-10-29
This msg. apperars also when you click left button on the clock applet and choose date/time prefs.
On every user account even on the first time  created user durning instalation.


Best regards
Pawel

---

### Post by ChrisNiemy on 2006-11-05
Hi!

This error is related with dbus and gnome-system-tools, and system-tools-backends under edgy.

Here in this bugreport:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946)
I wrote a comment, how for me this problem was fixed:

[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946/comments/32](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946/comments/32)

I quote it here:
> 


For me the error occured when I wanted to disable some services via "services-admin". Accidentally I unchecked dbus. And since there was the problem.

Fix:
Run Synaptic (should still work)
Re-Install following packages:
-gnome-system-tools
-system-tools-backend
-dbus
-libdbus-1-3
(or simply all packages in which names occur "dbus", don't know exactly, so I did)

Now try to run services-admin again and check that dbus there is enabled. Maybe Re-Login or Reboot is needed.

Hope this was helpful
Regards,
Chris


PS:
Now you need to run **alacarte** menu editor
and in the section >System >Administration
you must put **gksu** again back before the commands
gksu gdmsetup
gksu users-admin
gksu time-admin
gksu services-admin
gksu network-admin

---

### Post by dpf on 2006-11-07
I upgraded from verion 6.06 to version 6.10 on two systems.  I encountered these errors in both cases.  After trying almost everything, I decided to reinstall one of them from the 6.10 install cd.  Everything was great until I re-enabled the applications I personally installed in /usr/local.  It turned out for me that my copy of perl (in /usr/local/bin/perl) was the culprit.  It was in the path ahead of the delivered /usr/bin/perl.  Removing /usr/local/bin/perl and rebooting solved my problem on the fresh install and the upgraded install.

Personally, I think the delivered utilities should refer to the delivered perl explicitly to avoid this kind of thing.  Now I have to reinstall perl and have all of my apps look for it somewhere than /usr/local/bin/perl.  Hopefully this is something that can be addressed in future releases.

-dpf-

---

### Post by midtoad on 2006-11-08
thanks phansiizwe, that did the trick!

---

### Post by Fabiano Shark on 2006-11-15
Here is another way: Run **gksu users-admin** and give all privileges you want to your user. 

PS.: If you installed in OEM mode, run **sudo oem-config-prepare** to clean up the temporary files and reboot the system before doing it. ;)

---

### Post by Forgott3n on 2006-11-24
I am unable to get anything working through the command line or the GUI!

I have tried everyone's suggestions above but nothing seems to work.

even "gksu users-admin" doesn't work.

This became present from upgrading Dapper Drake to Edgy Eft.

---

### Post by ariadacapo on 2006-11-25
Same problem here after I unticked something in the "services" application (in the System > Administration menu) and it crashed.

Typing "gksu services-admin" results in

> 
GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(services-admin:5428): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
5428: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
5428: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:5428): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
5428: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library. 

and the usual "you are not allowed to access..." message.

---

### Post by Falconix on 2006-11-25
I'm where not able to run users and groups in dapper drake
My solution was to go and edit /etc/passwd manualy,
I removed characters on a users name which where not compatible.
In this case it was "é"

---

### Post by ttss82 on 2006-11-27
Has anybody found the solution yet?

I'v tried everything you mention and nothing works for me (I always get
message "You are not allowed to access the system configuration"), when
I  try to setup Networking in Administration panel.

Any help is welcome.

Tom

---

### Post by racoq on 2006-11-27
This problem also happens on Xubuntu, i've upgrade from Xubuntu 6.06 to 6.10, from the CD, and since that the only admin  graphic tool i can use is Synaptic. All other admin tools, say:

> 
The configuration Could not be loaded
You are not allowed to access the system configuration


Tried last night the solution posted by ChrisNiemy, and it worked

---

### Post by theonlydrayk on 2006-12-04
Ubuntu 6.10 fresh install (not upgrading)
I've got the same error message :

> The configuration Could not be loaded
You are not allowed to access the system configuration

When I run :
System->Administration->Services
System->Administration->Shared Folders
System->Administration->Time and Date
System->Administration->Users and Groups
System->Administration->Networking

The 'gksu' solution doesn't work for me.

After some search, i found the bug came from
the **System Communication Bus (dbus)** services
I open a terminal :

```
gksu synaptic
```

I re-install all packages with **dbus**
Now the services is started, everyting work.

I ran : 
System->Administration->Services
And check **System Communication Bus (dbus)** services
since re-install packages only run services
and do not re-activate it when I restart my computer.

I hope it will help you.

---

### Post by garcia.galili on 2006-12-05
I've been having what I think are the same problems; I've still got sudo privileges on the command line, but certain functions under System->Administration, which used to work fine, have been borked by the 6.10 upgrade.  The fix I've found, which I also posted on the related bugtrack ([https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/71102](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/71102)) is to first create the group admin

$ sudo groupadd admin

and then add your primary user to that group

$ sudo addgroup $USER admin

After a reboot, everything works fine.  Looks like something changed in the administration permission scheme in 6.10 but wasn't publicised.  Probably also related to this question:
[http://www.ubuntuforums.org/showthread.php?t=297135&highlight=reserved+admin](http://www.ubuntuforums.org/showthread.php?t=297135&highlight=reserved+admin)

Hope this helps,
 -Daniel

---

### Post by Xanf on 2006-12-17
I'm on Xubuntu.
Some month ago had this problem.
Reinstalling all "dbus" packages helped.
Now got the same error. Tried everything again - doesn't work anymore.
Any ideas? Maybe some of the latest updates again broke something?

---

### Post by garcia.galili on 2006-12-17
There's a fix in the works.  The bugtrack which I linked above has been folded in to [https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946) and patches are now making their way through testing in edgy-proposed.  For now, if you haven't done so already, your best bet is probably to try adding the admin group and adding your user to it as mentioned above.

 -Daniel

---

### Post by Xanf on 2006-12-18
2 Garcia.galili - didn't help: the user is already in that group (inherited from some earlier fight with that very problem).

BUT - I've got it fixed by combining all the above proposals (i.e. manually adding GKSUDO before all commands in admin menu via alacarte) + then disabling the dbus service + then deinstalling everything that is "dbus" + and then re-installing dbus again back.

So as a temporary workaround fix people can probably use my method. :-k

---

### Post by firer_av on 2006-12-20
Steps told my theonlydrayk worked for me fine on my ubuntu edgy. Reinstalling all the packges named 'dbus' should solve problem.

---

### Post by battra on 2006-12-26
According to the bug report (#59946), this problem has to do with a missing admin group.  Apparently, it happens when users do in place upgrades (e.g. apt-get dist-upgrade) since warty.  

To recap, my problem was that, when trying to access the administration tools like "System->Administration->Networking", I would receive this error:

"The configuration could not be loaded
You are not allowed to access the system configuration."

To solve:

1. Go to "System->Preferences->Menu Layout" and change the properties for "Users and Groups" from users-admin to gksudo users-admin.
2. Go to "System->Administration->Users and Groups" and add a new group called admin.  When creating the admin group, make sure your main user is checked.

This solved the problem and allowed me to access the "System->Administration" tools again (after being prompted for the sudo password).

---

### Post by Arawn on 2006-12-30
Hi!

I'm using Xubuntu Edgy, it was a fresh install,  and I have the same problem, I cannot access the admin utils through the menu. It happened a week ago or so, after a update. I've checked if the user is part of the admin group, which it is, I have re-installed dbus and system-tools related packages. The only thing I didn't do was the alacarte procedure, cause Xubuntu doesn't use alacarte. It didn't work.

I can open the utils by issuing sudo commands on a console, but I still have other problems, like every profile I had in network-admin disappeared, and even if I try to save one now, it won't save it (as in, it saves but doesn't store it, it's not there when I check).

Any ideas, as to solve this in Xubuntu? Thx.

---

### Post by M@htte0 on 2007-01-05
Hi, in Xubuntu, you can solve the problem manually editing the .desktop files that refer to the entries in the System sub-menu, which are in /usr/share/applcations

You have to do it with root permission. What you have to edit is the Exec entry, just adding ```
gksu 
``` before the application name

I hope it will never give any problem again!

---

### Post by coltrane on 2007-01-05
I've tried everything I've read so-far, the D-Bus service stars after reinstalling the D-Bus files.
But after restarting the PC I'm back to square one:- D-bus not running and no permission:confused:

---

### Post by Wight_Rhino on 2007-01-05
Any solutions?

I'm in the same boat, root doesn't have permission to open "users-admin" so none of the "gksu" solutions work. Just get the same message.. 

I'm already a member of the  "admin" group.

Anything else?

---

### Post by Arawn on 2007-01-08
Thanks, M@htte0, I didn't knew where the config files for the launchers where. But that only solves the problem of launching the admin tools in the menu, I have still the problem that network-admin doesn't use the network profiles I had setup for this user.

So, it seems my problem is one of permissions. Something has changed in a update, that removed the permissions for a admin user to access some locations where administrative information is.

Either it was on the admin group, or more general in the configuration...

Any ideas?

---

### Post by Arawn on 2007-01-09
Well, after reading this thread, [https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59946]("https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59946"), brought to attention before by garcia.galili, it seems to me that the problem lies with the security setting in d-bus (at least related to my problem, which is happening in a direct install of Xubuntu 6.10, and after a update). It might also be the problem affecting some of you to whom the previously presented solutions didn't work.

So, any  ideas?

---

### Post by Arawn on 2007-01-09
I think I solved this in Xubuntu, and I think it works also in Ubuntu. :D 

The problem is that the developers decided to change settings in the gnome-system-tools and d-bus access policy.

Whenever a user ran a admin utility, it ran under the user uid / admin group. Then, when commiting changes to configuration, it communicated through d-bus, and d-bus policy accepted because it's policy was to accept anything with a admin group permission. That's why most of you solved the (initial??) problem adding the user to this group.

Problem was that the developers found a security problem in gmome-system-tools, and decided to change the policy in d-bus to only accept root gid, and gnome-system-tools policy so that the utils had to be run with gksu, asking for the password and running them with root gid (please correct me if I'm saying anything wrong or missing something here, I'm no expert).

Since the menu didn't call with gksu but rather directly, it stopped working and started denying access. Hence the gksu solution.

My problem with the saved network profiles was simply solved. Since network-admin ran with root gid, I created the folder /root/.gnome2/network-admin-profiles, and copied the profiles there. It works. It couldn't create profiles, because the folder didn't exist.

Please do correct me if I'm wrong somewhere in this poor excuse of a explanation.

Thanks M@htte0, for the Xubuntu locations of the *.desktop files, so I could insert gksu.
Thanks Daniel (garcia.galili), for the bug #59946 link, and in that page the explanation on the gnome-system-tools and d-bus changes.

Hope this is fairly correct and does help any of you.

Cheers,
Ricardo

---

### Post by goonies on 2007-01-21
```
whonicca@carlisle:~$ gksu services-admin
(services-admin:4609): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(services-admin:4609): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
4609: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
4609: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:4609): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
4609: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.
```


what i did to fix the problem was

aptitude remove dbus

aptitude install dbus

I dont know if it was the right thing to do but it worked for me. Hopefully I did not cause more problems somewhere else by doing this.

---

### Post by yemartin on 2007-01-22
"aptitude remove dbus" may remove packages that depend on dbus. Instead, prefer:

```
aptitude reinstall dbus
```

Worked like a charm for me.

---

### Post by Kadmium on 2007-01-24
```
aptitude reinstall dbus
```

Worked for me too.

---

### Post by batman669 on 2007-02-12
Please help!

I have tried everything on this thread.  From adding gksu to making sure the user name is in the admin group to reinstalling dbus.

I am still having problems accessing administration configurations...

Any other suggestions?

Thanks,

_batman

---

### Post by tommyg on 2007-02-13
try:

```

sudo /etc/init.d/dbus start

```

Then, try to get into System --> Administration --> Services and make sure that "System communication bus (dbus)" is checked to start on boot.

Good luck!

---

### Post by batman669 on 2007-02-15
when i tried to start dbus i go the following :

* system message bus already started; not starting.
* Starting system message bus dbus

Also, when I (finally) got into Services, dbus was already checked.

Anything other suggestions??

---

### Post by girishv on 2007-03-08
Thanks martin, you saved me from a lot of frustration

girish

---

### Post by adssse on 2007-03-12
> **yemartin said:**
> "aptitude remove dbus" may remove packages that depend on dbus. Instead, prefer:

```
aptitude reinstall dbus
```



This worked for me as well. Many thanks...

---

### Post by JVAGO on 2007-03-18
Sorry for bumping up an old post but I too had this problem, my solution was

sudo /etc/init.d/dbus stop
sudo aptitude reinstall dbus
sudo /etc/init.d/dbus start

---

### Post by jeandersen on 2007-05-31
I still am having this same issue...

I even went so far as to uninstall dbus then reinstall dbus and gnome...

Any other suggestions...?


...

---

### Post by leguman on 2007-08-22
> **theonlydrayk said:**
> Ubuntu 6.10 fresh install (not upgrading)
I've got the same error message :



When I run :
System->Administration->Services
System->Administration->Shared Folders
System->Administration->Time and Date
System->Administration->Users and Groups
System->Administration->Networking

The 'gksu' solution doesn't work for me.

After some search, i found the bug came from
the **System Communication Bus (dbus)** services
I open a terminal :

```
gksu synaptic
```

I re-install all packages with **dbus**
Now the services is started, everyting work.

I ran : 
System->Administration->Services
And check **System Communication Bus (dbus)** services
since re-install packages only run services
and do not re-activate it when I restart my computer.

I hope it will help you.

that worked for me, thanks man :guitar:

---

### Post by kudos1uk on 2007-08-26
I did  all this and it looked like I fixed it, I could get into users& groups but clicked upgrade and 7.04 (fiesty) is available and when you click upgrade you get the same message....

---

### Post by jamvegan on 2007-08-27
> **kudos1uk said:**
> I did  all this and it looked like I fixed it, I could get into users& groups but clicked upgrade and 7.04 (fiesty) is available and when you click upgrade you get the same message....

Did you try the gksu thing with update-manager?

---

### Post by shak541 on 2007-09-21
OMG!! Thank you so much tommyg. Your way worked perfectly!!! I disabled some services and my computer was pretty messed up, but thanks to you it is back up and running again! :D !!!

---

### Post by ubifrost on 2007-10-29
I tried nearly all these solutions. At last, I just reinstalled (Xubuntu). In ten minutes I had my box back.
Eeaasy

---

### Post by brodiepearce on 2007-11-12
I'm experiencing this problem with Gutsy.... none of my services are starting on boot.  (As outlined in [this thread](http://ubuntuforums.org/showthread.php?t=610769)).  

Once I get into the GUI by starting GDM manually, I can access the services-manager after starting dbus manually as recommended in this thread, however, nothing is checked once I get to it, and it doesn't save my settings.  I.e. I check dbus and the other services I want started on boot (GDM cups etc. etc.), and close it, if I go back to it, everything is unchecked again.

This is my second or third fresh installation of Gutsy now, and the same problem is cropping up every single time, seemingly regardless of how I install my video drivers.  (Have tried latest fglrx (8.42.3), xorg-driver-fglrx in Ubuntu repositories, and now vesa).

---

