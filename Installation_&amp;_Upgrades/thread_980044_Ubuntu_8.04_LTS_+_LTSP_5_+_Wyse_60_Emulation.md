---
title: "Ubuntu 8.04 LTS + LTSP 5 + Wyse 60 Emulation"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by jc2it on 2008-11-12
I am writing this for two reasons, one I had to spend considerable time putting all of this together, and two I want to be able to reference what I did in the future.

Object: To make our Ubuntu 8.04 + LTSP 5 computer boot certain thin clients to a terminal emulator via telnet, and autoconnect to one of two different hosts. 

	I was told early on that it was not possible to make debian/ubuntu boot an LTSP thin client to anything but the GUI as default. This is not true. We are currently running Ubuntu 8.04 LTS with LTSP 5 and we boot several Thin clients (not all of them) to a terminal emulation program called wy60 that auto connects to another server running our ERP software over telnet. 

	Once LTSP is up and running on Ubuntu (there are plenty of other tutorials for this) you need to modify the chroot image location. Before this process I recommend backing up your image folders, especially if this is a working system, just in case a mistake is made.

```
$sudo cp -a /opt/ltsp /opt/ltsp-orig
```

	Next we will need to make sure your chroot environment is set up for installing the telnet software. We will do this by copying the resolv.conf and sources.list files from the main install to your chroot. This keeps things the same. Feel free to edit these for your environment if needed. 

```
$sudo cp /etc/resolv.conf /opt/ltsp/i386/etc/resolv.conf
$sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/sources.list
```

	Because I am using the wy60 terminal emulator package with a custom key map I need that in the chroot as well. When it is located in /etc it affects all users of the system. See [http://gutschke.com/wy60/](http://gutschke.com/wy60/) for more info. You may also need a terminfo file. Here is a couple of references to learn about them: [http://tldp.org/HOWTO/Text-Terminal-HOWTO-16.html](http://tldp.org/HOWTO/Text-Terminal-HOWTO-16.html) and [http://catb.org/terminfo/](http://catb.org/terminfo/) For my application I need the Wyse 50 terminfo file.

```
$sudo cp /etc/wy60.rc /opt/ltsp/i386/etc/wy60.rc
$sudo cp /usr/share/terminfo/w/wyse50 /opt/ltsp/i386/usr/share/terminfo/w/wyse50
```


	Now you must work as chroot. 

```
$sudo chroot /opt/ltsp/i386
```

	We want to first update the apt-get repository information. If you are used to using only synaptic then you might forget this step. Basically we are telling the chroot to download the available package lists from the repositories. 
```

#apt-get update
```

	Now we need to install the packages for telnet into the chroot. Make note of any errors you may have, as you may need to fix something after an install to chroot and the error messages are easier to get at this point.

```
#apt-get install telnet
#apt-get install wy60
```

	Now we must modify the default screen.d scripts to allow us to boot to the wy60 terminal emulator. We will start by using the default telnet script as our template. REMEMBER we are still in the chroot environment.

```
#cp /usr/lib/ltsp/screen.d/telnet /usr/lib/ltsp/screen.d/wy60
#vi /usr/lib/ltsp/screen.d/wy60
```

	Change these lines:

```
#
# Get this terminal name, to display on the top line of the screen
#
TTY=$(tty)
TTY=$(basename ${TTY})
if [ "${TTY}" = "console" ]; then
    TTY="tty1"              # Special case for first screen
fi

```
	To this:	NOTE: This change does part of the MAGIC that makes the proper SCREEN display as default. thanks Gadi from the #ltsp IRC channel on freenode.

```
# Get this terminal name, to display on the top line of the screen
#
#TTY=$(tty)
#TTY=$(basename ${TTY})
#if [ "${TTY}" = "console" ]; then
#    TTY="tty1"              # Special case for first screen
#fi

 TTY=$(tty)
 TTY=${TTY#/dev/tty}
 chvt ${TTY}
```

	And these lines:

```
    # Launch the telnet program.
    telnet ${TELNET_ARGS}
```

	To this:      NOTE: We are running wy60 in wyse50 mode you may not need this. See [http://gutschke.com/wy60/](http://gutschke.com/wy60/) for more info on the wy60 terminal emulator. 

```
    # Launch the telnet program.
    # telnet ${TELNET_ARGS}
    /usr/bin/wy60 --term wyse50 --command telnet ${TELNET_ARGS}

```

	Now we can leave the chroot environment, and build our new image.

```
#exit
$sudo ltsp-update-image
```

	Your lts.conf file must contain something like the following example. 

```
$sudo vi /var/lib/tftpboot/ltsp/i386/lts.conf

################
#lts.conf	
################
# default section is always required, even if empty.
#
        [default]

#       Section for wyse60 default terminals
#       These entrys take precedence over default
#       see: http//wiki.ltsp.org/twiki/bin/view/Ltsp/LtsConf
#
#       Select by MAC, DNS, or IP I use MAC cause it is on the side of my thin clients,
#	via network or physically looking
#	
#	If you specify a SCREEN_07=ldm in this section or a default section it will steal focus every time.
# 	So don't.
        [00:50:56:59:7F:81]
                SCREEN_03=wy60
                TELNET_HOST = 192.168.1.2
```

	You are now finished. Reboot the thin client and enjoy your brand new Wyse terminal emulator on Ubuntu 8.04 and LTSP 5.

---

### Post by ykanello on 2009-04-17
Very cool guide. 
I used it to add an old HP T5100 thin client in the configuration for text only support.
I had to also create accounts in the chroot environment, but it work great.
Thank you for the insight.
Y.

---

