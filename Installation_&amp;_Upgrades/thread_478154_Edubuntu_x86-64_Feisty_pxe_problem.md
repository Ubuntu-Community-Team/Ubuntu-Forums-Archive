---
title: "Edubuntu x86-64 Feisty pxe problem"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by clarknova on 2007-06-19
I'm running a fresh install of Edubuntu x86-64 Feisty server, 'out of the box'. When I try to boot a pxe client connected to the lan, the client gets an IP address, then I get this message:

[FONT="Fixedsys"]pxe-t01 file not found[/FONT]

and the client defaults to a local boot disk.

Interestingly, (perhaps) here is a clip from /etc/ltsp/dhcpd.conf on the server:

[FONT="Fixedsys"]if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
    filename "/ltsp/i386/pxelinux.0";
  }
  else{
    filename "/ltsp/i386/nbi.img";
  }
  option root-path "/opt/ltsp/i386";
}[/FONT]

None of these directory structures exist on this server:

[FONT="Fixedsys"]# ls /ltsp
ls: /ltsp: No such file or directory

# ls /opt/ltsp/
amd64

# find / -name pxelinux.0
/var/lib/tftpboot/ltsp/amd64/pxelinux.0
/opt/ltsp/amd64/usr/lib/syslinux/pxelinux.0
/opt/ltsp/amd64/boot/pxelinux.0[/FONT]

Always willing to try new things, I backup my dhcpd.conf file, substitute /opt/ltsp/amd64/boot/pxelinux.0" for "/ltsp/i386", and restart the dhcp server.

"File not found". No change.

Seems to me there should be an i386 directory in place of the amd64 directory, since I'm trying to boot an i386 client, no? Yes:

[FONT="Fixedsys"]# ltsp-build-client --dist i386
NOTE: adding default dist and components to security mirror:
[http://security.ubuntu.com//ubuntu](http://security.ubuntu.com//ubuntu) i386 main restricted
NOTE: Root directory /opt/ltsp/amd64 already exists, this will lead to problems, please remove it before trying again. Exiting.
error: LTSP client installation ended abnormally[/FONT]

Hmm. That didn't work. Google didn't help. Edubuntu Handbook doesn't seem to get into this, and not much relevant on ubuntu.com or edubuntu.org. Search of the forums doesn't shed any light.

Did I so something wrong? If I manage to build an i386 directory will this solve my problem? If so, then how? If not, then what?

I'm having a hard time believing  I'm the first person to try booting an i386 client off an amd-64 Feisty server, so did my install have a hiccup along the way?

Thanks.
db

---

### Post by clarknova on 2007-06-20
Turns out I was very close with that last comand.

[http://ubuntuforums.org/showthread.php?p=2881140](http://ubuntuforums.org/showthread.php?p=2881140)

---

### Post by hsweet on 2007-06-20
I had the same experience.  I don't think anyone uses LTSP with 64 bit clients, but there are lots of 64 bit servers so this must be a common problem. 

At the least their needs to be better ltsp edubuntu  docs.  At least explain all the ltsp-xxxx commands

Better yet would be if the 64 bit install script asks you about your client environment and installs the correct version.  Who to suggest this to?

---

