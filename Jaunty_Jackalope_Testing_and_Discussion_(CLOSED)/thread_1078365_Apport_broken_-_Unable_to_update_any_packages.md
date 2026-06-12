---
title: "Apport broken - Unable to update any packages"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Enmi on 2009-02-23
Yesterday... trued doing an update, and besides the inability to update Gstreamer bad plugins... Apport kinda killed the update progress. 

That was new.

Closed the update manager, and tried via synaptic. Same deal, apport wouldn't stop, thereby causing a fatal error to apt. 

Now, after several times of trying to get this to skip apport... I now have a broken apport package (apparently) along with synatic telling me I have to reinstall apport...

And when I try this from the command line, this is what I get:

```
~$ sudo /etc/init.d/apport stop
 * Stopping automatic crash report generation: apport             
/etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
```

I can't upgrade any packages. I can barely install new packages. It just keeps referring to this broken package which as bizarre enough as it is... will not update.

So far, previous to this quite horrible halt in any progress... Jaunty has quite met my expectations of a much MUCH slicker OS. Faster boot times are definitely apparent, even the desktop is a lot more responsive (heck, most apps take half as long to boot and show!).

Video's a bit wonky... probably due to the simple fact that I've been running on the open source ATI drivers, but effects are working fine.

My hardware specs are the following:
Gateway MX6708
Intel Centrino Duo 1.6GHz
ATI x1400 128 dedicated video
2Gb RAM
320GB SATA HDD - Partitions as follow:
 - /
 - /home
 - /winXP
 - /Data

This is an UPGRADED Ubuntu installation from 8.10 running dual boot Windows XP Pro.

I do not want to reinstall. I want to see if this can be fixed without going through that hassle. 

Any takers? Any attempts are great! [-o<

---

### Post by nanog on 2009-02-23
Repair broken upgrade

dpkg --configure -a

Repair broken package

sudo dpkg-reconfigure <package name>



- - - - - - - - - - - - -

Complete removal of package

sudo apt-get remove --purge <package name>

---

### Post by Enmi on 2009-02-24
> **nanog said:**
> Repair broken upgrade

dpkg --configure -a

Repair broken package

sudo dpkg-reconfigure <package name>



- - - - - - - - - - - - -

Complete removal of package

sudo apt-get remove --purge <package name>

Here goes nothin':
```
enmi@xxxx:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
enmi@Aasa:~$ sudo dpkg --configure -a
[sudo] password for enmi: 
dpkg: error processing apport (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apport
 apport-gtk
```

And

```
enmi@xxxx:~$ sudo dpkg-reconfigure apport
/usr/sbin/dpkg-reconfigure: apport is broken or not fully installed
```

The last line... the one that's been giving me the MOST headaches is the following:

```
enmi@xxxx:~$ sudo apt-get remove --purge apport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mcpp libglitz-glx1 gnome-bin libgnome32 gnome-libs-data libart2 snes9x-x
  libgnorbagtk0 libmcpp0 libgnomeui32 libglitz1 imlib-base liborbit0
  gdk-imlib11 libgnomesupport0 libgnorba27
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apport* apport-gtk*
0 upgraded, 0 newly installed, 2 to remove and 27 not upgraded.
2 not fully installed or removed.
After this operation, 688kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 186294 files and directories currently installed.)
Removing apport-gtk ...
Purging configuration files for apport-gtk ...
dpkg: error processing apport (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 apport
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The problem isn't repairing the broken packages... the problem is that the broken package prevents itself from being fixed! Apport won't be killed as a service, causes an error code 1, and the reinstall fails. 

Apport being the error generating and reporting program, installed as a service... and keeps FAILING to be removed. This is my problem, and because of this, now I can't do much of anything else as far as upgrading or updating packages. 

If I can MANUALLY remove or disable or just remove Apport from being loaded as a service, that MAY let me do something... but I'm not sure, considering the Alpha state of Jaunty. It keeps giving the error posted in the first post... and dpkg just kicks out the error code [1] as a result.

As you can tell, I'm not new to linux... or removing packages. I wouldn't have posted anything in the forums unless I'm seriously stuck and haven't found anything related to this either in the Ubuntu Forums, or online in general. I'm just new to this particular stump of an error that's driving me up the wall!

Help...? ;_;

---

### Post by Enmi on 2009-02-24
Anyone at all who could shed some light into how to do something about this problem?

---

### Post by Enmi on 2009-02-24
Well, I managed to run this bug over by following this simple and rather stupid little hack, pointed out at this website:
[http://www.digitalsanctum.com/2007/11/07/uninstalling-nginx-via-apt-get-stopping-nginx-invoke-rcd-initscript-nginx-action-stop-failed/](http://www.digitalsanctum.com/2007/11/07/uninstalling-nginx-via-apt-get-stopping-nginx-invoke-rcd-initscript-nginx-action-stop-failed/)

Went and opened up the apport init.d file,
sudo gedit /etc/init.d/apport
and added
"exit 0" without the quotes right below the script declarations, so it'd just quit out completely out of the script. This I did, of course, AFTER I forcibly removed apport from my services startup with:
sudo update-rc.d -f apport remove

As quoted by Shane from the site itself... sadly:
Pure hackery but it works.

Recap:
```
sudo update-rc.d -f apport remove
sudo gedit /etc/init.d/apport
 - Add "exit 0" right after script declarations... turns out to be line 17 or 18.
sudo apt-get update
sudo apt-get --reinstall install apport
```

Considering the fact that my computer is now a bit faster since not loading apport at startup... I think I'll leave it like that. XP 

This is NOT advisable under normal circumstances! I just don't care much for error reporting right now. >.>; But that's just me. I like the manual stuff personally.

---

### Post by nanog on 2009-02-25
next time just boot into tty -- no apport service. alternatively you can kill apport by 

 sudo /etc/init.d/apport stop.

if you are running jaunty you should fix apport so that you can contribute (or file a bug).

---

### Post by Enmi on 2009-02-26
> **nanog said:**
> next time just boot into tty -- no apport service. alternatively you can kill apport by 

 sudo /etc/init.d/apport stop.

if you are running jaunty you should fix apport so that you can contribute (or file a bug).

I tried killing apport using that command... it didn't seem to stop the service, and neither did it let me reinstall the service to let me upgrade the rest of my system. Because of the error generated (before I forced it to not load by using the exit: 0 hack), dpkg kinda fell over on itself and halted as you can see above.

I opened a bug report in Launchpad here:
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/333823](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/333823)

And apparently someone else got a similar issue yesterday. o_O

The funny thing is that this is basically an otherwise standard Intrepid install, upgraded to Jaunty. I don't like changing things if they work fine!

---

### Post by phorgan1 on 2009-03-05
I edited /etc/lsb-base-logging.sh where the real error is.  Other things from /sbin specify the path because the path is not set up. runlevel does not.  Change line 273 to:

        RUNLEVEL=`/sbin/runlevel | sed 's/^. //'`

and it solves the problem

Patrick

---

### Post by s.k.surat on 2009-04-03
> **phorgan1 said:**
> I edited /etc/lsb-base-logging.sh where the real error is.  Other things from /sbin specify the path because the path is not set up. runlevel does not.  Change line 273 to:

        RUNLEVEL=`/sbin/runlevel | sed 's/^. //'`

and it solves the problem

Patrick

Thanks and lot dude...:guitar:

---

