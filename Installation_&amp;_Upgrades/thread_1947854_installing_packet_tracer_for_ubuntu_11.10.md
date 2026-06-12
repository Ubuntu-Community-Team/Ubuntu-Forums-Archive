---
title: "installing packet tracer for ubuntu 11.10"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by murderd2death on 2012-03-27
So I downloaded Cisco's Packet Tracer 5.3.3 from their [Academy Connection]("http://cisco.netacad.net/cnams/content/templates/LibraryHome.jsp?#/resource/lcms/cnams_site/english/generic_site_areas/library/course_catalog/PTSoftwareDownloads_Students.html"), all attempts to install it seem to be futile. I've run a few combinations of code that I got from [this installation guide]("http://www.ubuntuka.com/run-cisco-packet-tracer-in-ubuntu/") with no avail. 

```
wintermute32@wintermute32-Lenovo-B570:~$ sudo dpkg -i PacketTracer-5.3-u.i386.deb
[sudo] password for wintermute32: 
dpkg: error processing PacketTracer-5.3-u.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 PacketTracer-5.3-u.i386.deb
wintermute32@wintermute32-Lenovo-B570:~$ chmod +x PacketTracer533_i386_installer-deb.bin
chmod: cannot access `PacketTracer533_i386_installer-deb.bin': No such file or directory
wintermute32@wintermute32-Lenovo-B570:~$ chmod +x PacketTracer53_i386_installer-deb.bin
chmod: cannot access `PacketTracer53_i386_installer-deb.bin': No such file or directory
wintermute32@wintermute32-Lenovo-B570:~$ chmod +x PacketTracer533_i386_installer-deb.bin
chmod: cannot access `PacketTracer533_i386_installer-deb.bin': No such file or directory
wintermute32@wintermute32-Lenovo-B570:~$ 

```

I have found another thread about installing Packet Tracer [here]("http://ubuntuforums.org/showthread.php?t=1923424&highlight=installing+packet+tracer"), but part of the guide includes installing wine. This is a bit disheartening, as I was hoping to be able to install this without getting into wine. Any of you guys have any ideas or help?

Regards

---

### Post by raja.genupula on 2012-03-27
have you tried that opening with software-center , i mean right click will give you that option in the file , what its giving you ?

---

### Post by murderd2death on 2012-03-27
> **raja.genupula said:**
> have you tried that opening with software-center , i mean right click will give you that option in the file , what its giving you ?

I have the files "PacketTracer533_i386_installer-deb.bin" and "PacketTracer533_Generic_Ubuntu.tar.gz" and I tried opening both in software center, and I get the response that neither file is a software package.

---

### Post by raja.genupula on 2012-03-27
if its a bin file then the installation should be like this
```
chmod +x filename.bin
./filename.bin
```

hope that helps . 
for your case
```
chmod +x PacketTracer533_i386_installer-deb.bin
./PacketTracer533_i386_installer-deb.bin
```
:)

---

### Post by murderd2death on 2012-03-27
> **raja.genupula said:**
> if its a bin file then the installation should be like this
```
chmod +x filename.bin
./filename.bin
```

hope that helps . 
for your case
```
chmod +x PacketTracer533_i386_installer-deb.bin
./PacketTracer533_i386_installer-deb.bin
```
:)

```
wintermute32@wintermute32-Lenovo-B570:~$ chmod +x PacketTracer533_i386_installer-deb.bin
chmod: cannot access `PacketTracer533_i386_installer-deb.bin': No such file or directory

```

do i need to get into the specific dir that the file is in? Usually when i install things from terminal this doesn't happen though.

---

### Post by raja.genupula on 2012-03-27
> do i need to get into the specific dir that the file is in?

Yes my friend .

---

### Post by murderd2death on 2012-04-02
> **raja.genupula said:**
> Yes my friend .

alright, the problem was just me being a doofus. the file was in the download folder, and i just relocated them to the home folder for a second and ran this command you gave me: 
```
chmod +x PacketTracer533_i386_installer-deb.bin
./PacketTracer533_i386_installer-deb.bin
```

packet tracer is working fine now, thank you :)

---

### Post by zaid zh on 2012-04-14
chmod: cannot access `Code::Blocks': No such file or directory

plz help me i'm lerning c++ in universty

---

### Post by pwieczkowski on 2012-05-09
If you are using Mozilla Firefox as your web browser, the default location for all downloads is: /home/USERNAME/Download, where USERNAME="your login credential or name".   I have had several problems using Ubuntu 12.04 LTS and UbuntuStudio 12.04.   I found the information on this web page written by KASL Network.

[http://kaslit.com/archives/installing-cisco-packettracer-5-3-2-on-64-bit-ubuntu-or-debian](http://kaslit.com/archives/installing-cisco-packettracer-5-3-2-on-64-bit-ubuntu-or-debian)

The article is well written and works according to the details.

---

