---
title: "Epson M1200 printer foomati-rip - failed"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by Jakim on 2012-06-20
Hi, i'm newly on ubuntu, but have a problem...Sorry for my basically english skill :)

I bought a new Epson M1200 printer and try to install on my ubuntu 10.04 lts version use the following instruction:

1. Download epsoneplijs-0.4.1.tgz -file from address [http://sourceforge.net/projects/epso...1.tgz/download]("http://sourceforge.net/projects/epsonepl/files/epsonepl/0.4.1/epsoneplijs-0.4.1.tgz/download")

2. From terminal, in the directory where you downloaded  epsoneplijs-0.4.1.tgz -file, type command: tar zxvf  epsoneplijs-0.4.1.tgz 

3. Go to directory epsoneplijs-0.4.1, which you just created, with command: cd epsoneplijs-0.4.1

4. Type command: ./configure --prefix=/usr

5. Type command: sudo make install

6. Download file: [http://www.nemesys.fi/tiedostot/ubun...200L-Hardy.ppd]("http://www.nemesys.fi/tiedostot/ubuntu/EPL-6200L-Hardy.ppd") 

7. Connect your printer to your computer and turn it on. (You can do it  in the beginning, but at least now you need it connected and powered  on.)

8. Go to System Settings &#8594; Printing &#8594; click “Add” and choose from the list Epson AL-M1200.

9. Click "Forward". Ubuntu searches for drivers for some time and then  gives “New printer”-window with the title “Choose driver”.

10. Tick the box "Provide PPD file” and navigate to the directory where you downloaded it and choose it.

11. Click "Open" and "Forward". Ubuntu asks if you want a test page.

but i click on test page appear a next error:

Print error There was the problem processing document 'Test Page' Idle - /usr/lib/cups/filter/foomatic-rip - failed

Please HELP!!!!

---

