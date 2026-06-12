---
title: "revert back to usb stick from usb zip"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by harshaambati on 2010-10-03
hello every one 

I used mkdiskimage command to convert my usb stick to usb zip using the following procedure 
# mkdiskimage -4 /dev/sdx 0 64 32

[http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/]("http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/")

now i would like to revert back to using usb stick as boot option rather than as usb zip

so can anyone help 

thanks

---

### Post by harshaambati on 2010-10-04
actually i have the solution for this problem 

just wrote the mbr with zeros

# dd if=/dev/zero of=/dev/hda bs=512 count=1

---

