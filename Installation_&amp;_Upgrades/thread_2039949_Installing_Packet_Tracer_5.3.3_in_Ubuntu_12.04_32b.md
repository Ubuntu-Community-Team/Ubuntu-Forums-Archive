---
title: "Installing Packet Tracer 5.3.3 in Ubuntu 12.04 32bit"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by jerryjohn17 on 2012-08-09
hello im using ubuntu 12.04 
but i can't install PacketTracer533_i386_no_tutorials_installer-deb.bin

i used the command that i saw in this forum but i wont work..

chmod +x PacketTracer533_i386_no_tutorials_installer-deb.bin

PacketTracer533_i386_no_tutorials_installer-deb.bin : command not found 

:'(
help guys.. 

thanks.. :(

---

### Post by pipe1984 on 2012-09-04
Hello. Try this:

Type "sudo chmod +x filename.bin" without quotes, replacing "filename.bin" with the actual name of the BIN file that you want to install. Press "Enter." Enter your password if prompted and press "Enter" again.


Type "./filename.bin" without quotation marks, again replacing "filename.bin" with the name of the file you're installing. Press "Enter" to run the program. Follow any instructions that appear within the terminal during the installation process.

---

### Post by Synoc on 2013-04-17
as a side note. the version I downloaded for packettracer 5.3.3 was "Packet Tracer v5.3.3 Application only Linux-Ubuntu.bin." the ONLY way I got this to run was to rename AND chmod it

```

chmod 774 /path/to/file/Packet Tracer\ v5.3.3\ Application\ only\ Linux-Ubuntu.bin
mv /path/to/file/Packet\ Tracer\ v5.3.3\ Application\ only\ Linux-Ubuntu.bin /path/to/file/PacketTracer.bin
cd /path/to/file
./PacketTracer.bin

```
if you navigate to the file first you can save yourself some typing obviously, but if I were to use the file as it was given I kept getting "no file or directory" errors.

---

### Post by jon712 on 2013-12-09
first step: download the PT files 
choose the .bin file
then rename the file with extension .bin
at the terminal

type sudo su
       cd Downloads
       ls
       chmod +x Cisco.bin 

this command will make the Cisco.bin will turn green

then type ./Cisco.bin
press enter

then press Y to accept the terms and condition of EULA

it works for me, Hope this will help you out.

---

