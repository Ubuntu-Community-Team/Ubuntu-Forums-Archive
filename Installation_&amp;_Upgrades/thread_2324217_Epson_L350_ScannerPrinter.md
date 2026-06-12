---
title: "Epson L350 Scanner/Printer"
date: 2016-05-11
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2016-05-11
I had installed the Epson L350 Scanner/Printer at 14.04, but on 15.10 I fail to get the scanning part to work.

I tried to install the scanner driver from Epson

I switch to the directory:
cd iscan-bundle-1.0.0.x64.deb/
sudo dpkg -i data/iscan-data_1.36.0-1_all.deb 
sudo dpkg -i core/iscan_2.30.1-1~usb0.1.ltdl7_amd64.deb 
sudo dpkg -i plugins/iscan-network-nt_1.1.1-1_amd64.deb 

Simple scan did not find the scanner.

sudo apt-get install sane sane-utils libsane-extras xsane

sudo sane-find-scanner 
found USB scanner (vendor=0x04b8 [EPSON], product=0x08a1 [EPSON L350 Series]) at libusb:001:007
could not fetch string descriptor: Pipe error

sudo scanimage -L
device `epkowa:usb:001:007' is a Epson (unknown model) flatbed scanner

according to the found scanner in sane-find-scanner I edited the line in /etc/sane.d/epson.conf
usb to 
usb 0x04b8 0x08a1

Simple Scan says now under Source: Epson (unknown model) - Scanning results in Unable to connect to scanner

Image Scan!
results in an iscan titled window with "Could not send command to scanner. Check the scanner's status.

Xscan
Failed to open device `epkowa:001:007'


On a mounted drive I have the old files of 14.04 preserved.

What can I do to get the scanner working again?

---

