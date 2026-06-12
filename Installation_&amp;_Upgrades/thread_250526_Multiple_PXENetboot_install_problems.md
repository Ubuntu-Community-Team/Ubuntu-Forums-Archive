---
title: "Multiple PXE/Netboot install problems"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by amagi on 2006-09-04
I have tried to do PXE installs on both fedora and recently ubuntu and I can not get it to work.

I used Ethereal/wireshark to analyse the messages on the network in order to get more info but I can not seem to get any useful info from it regarding the problem.

FIRST ISSUE:

I have one computer which has a PXE enabled network card. I have configured DHCP3 and in ethereal I am seeing the computer making the DHCP discover request and my DHCP server giving the DHCP offer with all the required info (router, next-server, filename). But the computer keeps on telling me that it did not receive a bootfile. There are no TFTP requests on the network so I guess it just does not like the filename. If I use another computer with a tftp client I can get the filename so I know TFTP is working fine.


SECOND ISSUE:

I have another computer with which I use a bootrom floppy to try and start the net install. This bootflop does all the DHCP and TFTP stuff correctly so I was really exited.
To install the system I copied all the contents of the Ubuntu Dapper disk into /var/www/ubuntu and started apache. I can browse the contents of the disk with other computers so apache is working fine. When I select the 'enter own mirror' option in the installation process and enter the address of the server and the /ubuntu/ directory the client retrieves the Release and Release.gpg file from the server (can see that in wireshark) but after that the client gives me an error message that it was not able to retrieve the required files!!!

Can someone explain me what I am doing wrong here or is it not possible to use the CD as a local 'mirror' for the installation process?

---

### Post by ArneLovius on 2006-10-04
have a look in your apache error.log to see what file it is failing to download. I'm going to guess its a binutils file

---

### Post by amagi on 2006-10-05
Just want to reply to myself because I found the solution which might be of interest to other people facing the same problems. It was very hard to find, but on one site (sorry I can not remember which one) there was some info on the DHCP config which triggered the PXE network boot for the network card I had. My config is now as follows:

```

	hardware ethernet 00:90:27:72:e9:23 ;
	option host-name "ubuntu1";
	fixed-address 172.16.3.15;
	filename "pxelinux.0";
	option bootfile-name "pxelinux.0";
	next-server 172.16.3.5;
	server-identifier 172.16.3.5;
	option vendor-class-identifier "PXEClient:Arch:00000:UNDI:002001";
	option vendor-encapsulated-options 09:0f:80:00:0c:4e:65:74:77:6f:72:6b:20:62:6f:6f:74:0a:07:00:50:72:6f:6d:70:74:06:01:02:08:03:80:00:00:47:04:80:00:00:00:ff;

```

The last two options were required for me. The first one is mentioned in more documentation (the vendor-class-identifier) but the last one was no where to be found. 
I have no idea what the 'vendor-encapsulated-options' does, but it worked for me and the card booted the PXE way right away.

There was also another problem I had with the TFTP server where it did not find a boot file. This was because the network adapter sended a strange request with some octal code after the filename which confused the TFTP server. I found a script for that to on the net.
Create a filename called /etc/tftp.remapping with the following contents:
```

# strip ending garbage from filenames (Realtek PXE bug)
r ^([[:graph:]]*)(.+)$ \1

```
This file uses regex to change tftp requests before they are handled by the tftp server and in this case strips of the strange characters.
The next step is to initialise the tftp server to use the remapping file by editing the /etc/xinet.d/tftp file:
```

service tftp
  {
        disable                 = no
        socket_type             = dgram
        wait                    = yes
        user                    = root
        server                  = /usr/sbin/in.tftpd
        server_args             = -v -s /var/lib/tftpboot -m /etc/tftp.remapping
        only_from               = 172.16.3.0/24
        interface               = 172.16.3.5
  }

```

For the other problem of not being able to use the CD. Maybe I was stuppid but nowhere it was mentioned that you can not use the Ubuntu Live CD for this kind of installation. As soon as I downloaded the Alternative CD and made its contents available through apache the installation accepted it as a local mirror and I could continue.

Hope this helps people experimenting with PXE. It gave me a lot of headaches but finally it worked.

---

### Post by CHR1Six on 2006-11-08
I experienced a problem like your second issue; however, it went away once I downloaded the "other installation methods" ISO rather than the normal ISO. I have run into a new net installation problem now which seems to be affecting a couple of other people too. Maybe Amagi can shed some light on this. :)

[http://ubuntuforums.org/showthread.php?t=289215&highlight=PXE]("http://ubuntuforums.org/showthread.php?t=289215&highlight=PXE")
[http://ubuntuforums.org/showthread.php?t=293866&highlight=PXE]("http://ubuntuforums.org/showthread.php?t=293866&highlight=PXE")

---

