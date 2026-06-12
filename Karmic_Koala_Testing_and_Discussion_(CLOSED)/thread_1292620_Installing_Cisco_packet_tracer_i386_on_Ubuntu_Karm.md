---
title: "Installing Cisco packet tracer i386 on Ubuntu Karmic amd64"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bogdanbiv on 2009-10-16
Hello,

I'm a Cisco CCNA student and I'd like to install Cisco Packet tracer on my PC. It's a tool that simmulates/emmulates working on a computer network with all the routers, servers, desktops, cables and so on.
The problem is that I have amd64 architecture and the installer is a self extracting archive (.bin file) that contains a i386 Debian package.

Here is a dump from the console:
```
You have accepted the terms to the EULA. Cisco Packet Tracer will now be installed.
Attempting to install package now
dpkg: error processing PacketTracer-5.2-u.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.2-u.i386.deb
```

I also tried to launch the installer with the linux32 command:
*linux32 sh cisco_pt.bin* but it fails with the _same_ error.

They also provide a tar.gz installer but that is broken too.
I've tried to edit the installer to correct the errors indicated by bash, but it still does not install the application correctly.


Another route, I think, would be to see where the self-extracting archive stores the deb and catch & copy the deb, unpack it and repackage for amd64.

UPDATE: How to get the .deb file:
Open the bin file in a text viewer/editor ( vim PacketTracer52_i386_installer-deb.bin )
Look for the line where they hold the temporary extract directory "export TMPDIR=`mktemp -d /tmp/selfextract.XXXXXX`"
Run the self extracting archive and before you accept the EULA go to the /tmp/selfextract.XXXXXXX dir and copy the file from there.

Note: After the user accept the EULA and before it terminates execution, the script quickly deletes the temporary directory. Copy the file before you accept EULA!

---

### Post by bogdanbiv on 2009-10-16
I found the temp dir in which the bin extractor stored the i386 .deb file and I copied it. I guess the rest is about repackaging the deb for 64bit.

---

### Post by P4man on 2009-10-16
have a look here:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by ProgramErgoSum on 2009-10-16
If Wine is an option check this: [Running Cisco Packet Tracer in Linux]("http://www.linuxscrew.com/2007/10/16/running-cisco-packet-tracer-in-linux/").

---

### Post by bogdanbiv on 2009-10-16
No need for any other quircks, it's solved. After
```
sudo dpkg -i --force-all PacketTracer-5.2-u.i386.deb

# aftet install the symbolic link to the executable script points to /opt/pt, but my /opt/pt is empty so the link is broken
# To correct this remove the link and make another that points to /usr/local/PacketTracer5/packettracer
sudo rm /usr/local/bin/packettracer
sudo ln -s /usr/local/PacketTracer5/packettracer

#start the program with bash
bash packettracer
```


After starting the program I added a few devices, added a link between them.
I was able to bring the link up. I saved the file, closed the program and brought it back up. It was able to read the previously saved file.

---

### Post by zekkerj on 2009-10-21
> **bogdanbiv said:**
> No need for any other quircks, it's solved. After
```
sudo dpkg -i --force-all PacketTracer-5.2-u.i386.deb

# aftet install the symbolic link to the executable script points to /opt/pt, but my /opt/pt is empty so the link is broken
# To correct this remove the link and make another that points to /usr/local/PacketTracer5/packettracer
sudo rm /usr/local/bin/packettracer
sudo ln -s /usr/local/PacketTracer5/packettracer

#start the program with bash
bash packettracer
```
After starting the program I added a few devices, added a link between them.
I was able to bring the link up. I saved the file, closed the program and brought it back up. It was able to read the previously saved file.

Hi,

Didn't it complained about missing libraries?
```
/usr/local/PacketTracer5/bin/PacketTracer5: error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory

```

I solved it using LD_LIBRARY_PATH to force use of the QT library shipped with PT ($PTHOME/lib), but, gee, this is ugly...

Does any one knows how can I install the i386 version of QT library in my jaunty [soon karmik] amd64 box???

---

