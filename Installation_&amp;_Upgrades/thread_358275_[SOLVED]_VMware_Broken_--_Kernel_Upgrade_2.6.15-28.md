---
title: "[SOLVED] VMware Broken -- Kernel Upgrade 2.6.15-28-386"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2007-02-10
My father recently upgraded his kernel to 2.6.15-28-386. The only problem is, his VMWare kernel-modules is only for 2.6.15-27-386. So I edited his /boot/grub/menu.lst file and commented out all the references to 2.6.15-28, so it could fall back to 2.6.15-27.

It worked, but now VMware seems to be broken. I removed VMWare and ran "sudo rm -rf /etc/vmware", but that didn't seem to make the uninstall any better. I've tried many many things, but this is the last bit of my terminal output... what can I do?

```
**rod@hppavilion503n:~$ sudo dpkg -rf vmware-player**
dpkg: conflicting actions --field and --remove

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rod@hppavilion503n:~$ sudo aptitude reinstall vmware-player
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  vmware-player
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
[B]rod@hppavilion503n:~$ sudo mkdir /etc/vmware
rod@hppavilion503n:~$ sudo aptitude reinstall vmware-player[/B]
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  vmware-player
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.132.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.238.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
**rod@hppavilion503n:~$**

```
```
**rod@hppavilion503n:~$ uname -r**
2.6.15-27-386

```

---

### Post by altonbr on 2007-02-10
bump.

---

### Post by Tanker Bob on 2007-02-10
In your terminal, try running:

> 
cd /usr/bin
sudo ./vmware-config.pl


Follow the prompts.  It will recompile vmware for the new kernel.  You have to do this every time that you upgrade a kernel.  If the script cannot stop all the vmware services, then restart the system and try again right away.

I've updated the kernel twice now and this worked for me.  Supposedly VMWorkstation 5.5.3 is compatible up to ubuntu 6.06.  I'm using it with 6.10 and kernel 2.6.17-11 and it works so far.

---

### Post by altonbr on 2007-02-11
The only programs I have in /usr/bin related to VMWare are:
*vmnet-bridge, vmnet-dhcpd, vmnet-natd, vmnet-netifup, vmnet-sniffer, vmplayer, vmstat, vm-support, vmware-config-network.pl & vmware-ping*

---

### Post by Tanker Bob on 2007-02-11
Are you using VMWorkstation 5.5x?  If so, you should have a number of other scripts there, including vmware-config.pl.  However, looking at your file list, I would recommend trying vmware-config-network.pl.

---

### Post by Gendo2 on 2007-02-11
Hi,

I've got exactly the same problem using Ubuntu Dapper with the VMware Player out of Synaptic. 


./vmware-config.pl doesn't work for me either (doesn't exist)

I guess this is only availible if you have the Workstation or the Server and not the Player.
 
vmware-config-network.pl doesn't work :/

I think the problem is with the kernel modules 

After deleting it and reinstalling i saw that he takes this kernel:
vmware-player-kernel-modules-2.6.15-27

The newest Ubuntu is 2.6.15-28


Any idea how I can get the newest? (I don't have Workstation or Server)

Greetings

---

### Post by sleepytom on 2007-02-11
I'm having the same problem after doing a routine update via synaptic. When I try to run the config routine, I get an error that the headers cannot be found, as follows:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```


I tried putting in the following directory, but it didn't work:


```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.15-27-386/include

The directory of kernel headers (version 2.6.15-27-386) does not match your
running kernel (version 2.6.15-28-386).  Even if the module were to compile
successfully, it would not load into the running kernel.
```


Help :(

---

### Post by Gendo2 on 2007-02-11
I've found a pretty nice howto. i still test it so no warranty :) (2nd post should be the better one but i don't have make-kpkg maybe someone has there an idea too?)

[http://ubuntuforums.org/archive/index.php/t-216233.html](http://ubuntuforums.org/archive/index.php/t-216233.html)

---

### Post by Tanker Bob on 2007-02-11
> **sleepytom said:**
> I'm having the same problem after doing a routine update via synaptic. When I try to run the config routine, I get an error that the headers cannot be found, as follows:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```

:SNIP:

Help :(
Sounds like your problem isn't with VMWare but with your kernel installation.  I had to run through the same routine with vmware-config.pl after the kernel update this weekend, but all the directories and files exist.  You probably need to download your kernel header packages, but I'm new to Linux and have no idea which specific packages you need.  You may want to download the latest VMWorkstation or VMPlayer manual.  They may have more detailed information on the packages necessary to run the scripts.

---

### Post by Gendo2 on 2007-02-11
hmm after trying the howto it said that the vmmon was to new.. so now i'm ujst trying to install vmware player from [www.vmware.com](www.vmware.com)

within this installtion it created automatically a new vmmon and vmnet.

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

i put it into /tmp

tar -xzf VMware-player-1.0.3-34682.tar.gz
cd vmware-player-distrib
sudo ./vmware-install.pl

It will complie a new kernel and the vmmon thing (just accept everything)

Hope that works with u too. My Player is running now :)

---

### Post by sleepytom on 2007-02-11
Okay, so I ran this code:

```
sudo apt-get install linux-headers-386
```

and then ran the vmware configuration again:

```
sudo /usr/bin/vmware-config.pl
```

And things work perfectly.

Thanks for your help

---

### Post by Tanker Bob on 2007-02-11
> **sleepytom said:**
> 
Thanks for your help
You're very welcome.  I'm glad that is worked out for you.

---

### Post by altonbr on 2007-02-12
I'm simply using VMWare player from the repositories. Like I said, it works to comment out any reference to 2.6.15-28 in GRUB, and revert back to 2.6.15-27 so it matches with the vmware-player-kernel-modules. I will wait for the Ubuntu team to upgrade the vmware-player-kernel-modules package, then erase the commented lines in GRUB and everything will be as good as new.

I could installed the new VMWare player 1.03 but I like doing everything from the repositiories, thanks.

---

### Post by Tanker Bob on 2007-02-12
If you simply force-reinstall VMWare player from the repositories under the new kernel (or uninstall then reinstall), the player installation should recompile itself unless the app has been precompiled for the repository.

---

### Post by altonbr on 2007-02-12
VMWare downloads the vmware-player-kernel-modules dependancy, but it's only at 2.6.15-27 and NOT 2.6.15-28 so that cannot be done.

---

### Post by maraschin on 2007-02-13
This is bad!
I've the same problem...
After upgrade the kernel vmware player stoped.
There is module for the new kernel.. and I'm talking about Dapper a version that should be "stable"!
I agree that it does still work with the old kernel version, but that is clear a broken dependence :-/

---

### Post by Tanker Bob on 2007-02-13
> **maraschin said:**
> This is bad!
I've the same problem...
After upgrade the kernel vmware player stoped.
There is module for the new kernel.. and I'm talking about Dapper a version that should be "stable"!
I agree that it does still work with the old kernel version, but that is clear a broken dependence :-/

It's not a dependence issue.  Simply download the current version of Player from VMWare, uninstall the old version and install the new one.

---

### Post by talking_walnut on 2007-02-13
> **sleepytom said:**
> Okay, so I ran this code:

```
sudo apt-get install linux-headers-386
```

and then ran the vmware configuration again:

```
sudo /usr/bin/vmware-config.pl
```

And things work perfectly.

Thanks for your help



Just wanted to say that this worked for me too.  I'd say it'd work for everyone. After I updated the kernel, Vmware had to be reconfigured. I was getting this error: ```
None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?
``` 
After hitting yes to that it asked me ```
What is the location of the directory of C header files that match your running
kernel?
``` I was stuck here until I installed the headers as above. 

Hope this helps someone :)

Edit: I'm running Vmware Server

---

### Post by Lucas2005 on 2007-02-14
> **sleepytom said:**
> Okay, so I ran this code:

```
sudo apt-get install linux-headers-386
```

and then ran the vmware configuration again:

```
sudo /usr/bin/vmware-config.pl
```

And things work perfectly.

Thanks for your help


This worked for me too, it fixed this problem i was getting

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.
```

---

### Post by nuclearj on 2007-02-17
> **sleepytom said:**
> Okay, so I ran this code:

```
sudo apt-get install linux-headers-386
```

and then ran the vmware configuration again:

```
sudo /usr/bin/vmware-config.pl
```

And things work perfectly.

Thanks for your help

This is the golden ticket.  Worked like a charm.  I guess when you update the kernal, you have to update vmwares stuff too.  Is that accurate?  I'm a total noob so sorry if i state the obvious.

---

### Post by jacksonz123z on 2007-02-17
You need to download the current kernel headers "sudo apt-get install linux-headers-$(uname -r)" then reconfigure vmware with "/ust/bin/vmware-config.pl".  This has always fixed the problem for me.  Have a look at virtualbox, looks very good!

---

### Post by lunatc on 2007-02-22
The vmmon.ko and vmnet.ko from 2.6.15.27 seems to work with 2.6.15.28

I have created a new vmware-player-kernel-modules .deb for this new kernel based on then previous version:

> #!/bin/bash
sudo /etc/init.d/vmware-player stop
mkdir tempo
cd tempo
# If not in /var/cache/apt/archives...
sudo aptitude download vmware-player-kernel-modules-2.6.15-27
# cp /var/cache/apt/archives/vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb ./
ar xv vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb
rm vmware-player-kernel-modules-2.6.15-27_2.6.15.10-10_i386.deb
mkdir DEBIAN
tar xvfz control.tar.gz -C DEBIAN/
tar xvfz data.tar.gz
rm control.tar.gz data.tar.gz debian-binary
pushd lib/modules/
for I in *; do mv $I $(echo $I | sed -e "s/27/28/"); done
popd
pushd usr/share/doc/
mv vmware-player-kernel-modules-2.6.15-27 vmware-player-kernel-modules-2.6.15-28
popd
sed -i -e "s/2\.6\.15-27/2\.6\.15-28/g" -e "s/2\.6\.15\.10-10/2\.6\.15\.10-11/g" DEBIAN/control
for I in $(find lib/ usr/ -type f);  do md5sum $I; done > DEBIAN/md5sums
cd ..
dpkg-deb -b tempo
mv tempo.deb vmware-player-kernel-modules-2.6.15-28_2.6.15.10-11_i386.deb
rm -rf tempo/
sudo dpkg -i vmware-player-kernel-modules-2.6.15-28_2.6.15.10-11_i386.deb
sudo /etc/init.d/vmware-player start


---

### Post by altonbr on 2007-02-24
Like I may have said, if you're running VMWare-Player and don't have that config executable to run, try commenting out the new kernel in /boot/grub/menu.lst and then reinstalling VMWare-Player

```
$ sudo gedit /boot/grub/menu.lst
```
[LIST]
[*]Edit out the newest kernel with pound signs (#)
[/LIST]

```
$ sudo aptitude remove vmware-player && sudo aptitude install vmware-player
```
[LIST]
[*]This will force VMWare-Player to run with the kernel you booted into.
[*]This means, for me, the kernel is now 2.6.15.27 and not 2.6.15.28 because 2.6.15.28 doesn't have the proper kernel-headers for VMWare
[/LIST]

Good luck!

---

### Post by JoxBG on 2007-03-01
If you're running VMWare-Player and don't have that config executable to run, just install the latest vmplayer so you don't have to keep going back to 2.6.15-27. 

What I did:

1. Get the current kernel-headers, there are posts above (jackson's) on how to do this.
2. If you installed vmplayer from Synaptic, uninstall using same. Then clean out /etc/vmware, else installation of new player will fail as it detects a previous installation (I just renamed mine to oldvmware, ie. sudo mv /etc/vmware /etc/oldvmware).
3. Follow Gendo2's process:
     - download new vmplayer from vmware site.
     - put it into /tmp
     - tar -xzf VMware-player-1.0.3-34682.tar.gz
     - cd vmware-player-distrib
     - sudo ./vmware-install.pl

4. If you opt not to run vmware-config.pl as part of vmware-install.pl then invoke vmware-config.pl. This will rebuild, install and test new vmmon and vmnet modules.
5. Next time, if you need to reconfigure, you have an existing vmware-config.pl in /usr/bin  :) . And you can enjoy the latest kernel too.

HTH,
Jox

---

### Post by mrbhave on 2007-03-03
Running Herd 4, this worked for me:
```
sudo apt-get install linux-headers-$(uname -r)
sudo /usr/bin/vmware-config-network.pl
```

---

### Post by askoranswer on 2007-03-07
> **JoxBG said:**
> If you're running VMWare-Player and don't have that config executable to run, just install the latest vmplayer so you don't have to keep going back to 2.6.15-27. 

What I did:

1. Get the current kernel-headers, there are posts above (jackson's) on how to do this.
2. If you installed vmplayer from Synaptic, uninstall using same. Then clean out /etc/vmware, else installation of new player will fail as it detects a previous installation (I just renamed mine to oldvmware, ie. sudo mv /etc/vmware /etc/oldvmware).
3. Follow Gendo2's process:
     - download new vmplayer from vmware site.
     - put it into /tmp
     - tar -xzf VMware-player-1.0.3-34682.tar.gz
     - cd vmware-player-distrib
     - sudo ./vmware-install.pl

4. If you opt not to run vmware-config.pl as part of vmware-install.pl then invoke vmware-config.pl. This will rebuild, install and test new vmmon and vmnet modules.
5. Next time, if you need to reconfigure, you have an existing vmware-config.pl in /usr/bin  :) . And you can enjoy the latest kernel too.

HTH,
Jox

Hello,

I have done all of the above and seemed all went fine (no errors through the install process).
I tried to open an appliance, it looked like it is going to start but nothing started. The same when tried to start the player alone.
Attempting to start the player from the console i got the following:
~$ vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmplayer: symbol lookup error: /usr/lib/libbonobo-activation.so.4: undefined symbol: g_get_language_names

Thanks

---

### Post by askoranswer on 2007-03-07
I have tried the following:
just copy the /usr/lib/libpng12.so.0 to /usr/lib/vmware/lib/libpng12.so.0/ 
and now i only get this:
~$ vmplayer
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmplayer: symbol lookup error: /usr/lib/libbonobo-activation.so.4: undefined symbol: g_get_language_names

And the vmplayer doesn't start

---

### Post by askoranswer on 2007-03-07
Now if i start vmplayer with the following command:
VMWARE_USE_SHIPPED_GTK=yes vmplayer 
i only get this:
~$ VMWARE_USE_SHIPPED_GTK=yes vmplayer
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmplayer: symbol lookup error: /usr/lib/libbonobo-activation.so.4: undefined symbol: g_get_language_names

And wmplayer still doesn't start

---

### Post by askoranswer on 2007-03-08
Finaly i found a workaround

from the [http://www.vmware.com/community/thread.jspa?threadID=38856&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=38856&tstart=0)
i do the previously mentioned:
just copy the /usr/lib/libpng12.so.0 to /usr/lib/vmware/lib/libpng12.so.0/ 
and from the [http://ubuntuforums.org/archive/index.php/t-189623.html](http://ubuntuforums.org/archive/index.php/t-189623.html)
i run the vmplayer, after unsetting the GTK_MODULES variable:
$ unset GTK_MODULES
$ vmplayer

Now the vmplayer will start

Thank you all

---

### Post by altonbr on 2007-03-13
Kernel-modules now updated to 2.6.15-28-386 :D (In Dapper at least)

---

