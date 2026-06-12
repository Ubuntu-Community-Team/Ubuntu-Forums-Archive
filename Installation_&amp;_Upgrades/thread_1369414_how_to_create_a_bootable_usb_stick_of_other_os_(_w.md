---
title: "how to create a bootable usb stick of other os ( window 7) in Ubuntu 9.10"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by elaine81 on 2009-12-31
Hi all , 

 trying to create a bootable usb stick of other os ( window7)  in Ubuntu 9.10 , anyone can advise me how to go abt it ? thankss!!:guitar::guitar:

---

### Post by snakeman21 on 2010-01-01
I have not tried it with Windows 7, but I did a lot of research and a lot of work at it with XP.  As far as I know, there is currently no (known) way of doing it.  If I am wrong, someone please correct me!

---

### Post by presence1960 on 2010-01-01
[http://www.eeeguides.com/2007/12/install-windows-vista-from-usb-flash.html](http://www.eeeguides.com/2007/12/install-windows-vista-from-usb-flash.html)

That is a method to create a bootable USB for Vista. Should work with Windows 7. Save yourself some trouble and use an 8 GB stick. If you use a 4 GB stick that is not large enough as the win 7 image is bigger than that and you will have to use vLite to trim it down.

BTW I used the how to  on making a bootable USB for XP and it worked. I used it to install XP with no problems. Don't panic that the web page is for an Asus EEE PC. It works for all PCs.

**EDIT:** I just noticed you want to do it in Ubuntu- unfortunately that is not possible. Must be done on a windows machine.

---

### Post by elaine81 on 2010-01-01
> **presence1960 said:**
> [http://www.eeeguides.com/2007/12/install-windows-vista-from-usb-flash.html](http://www.eeeguides.com/2007/12/install-windows-vista-from-usb-flash.html)
 
That is a method to create a bootable USB for Vista. Should work with Windows 7. Save yourself some trouble and use an 8 GB stick. If you use a 4 GB stick that is not large enough as the win 7 image is bigger than that and you will have to use vLite to trim it down.
 
BTW I used the how to on making a bootable USB for XP and it worked. I used it to install XP with no problems. Don't panic that the web page is for an Asus EEE PC. It works for all PCs.
 
**EDIT:** I just noticed you want to do it in Ubuntu- unfortunately that is not possible. Must be done on a windows machine.
 
Nope , dun work , Win 7 stuck at "expanding files" , sometime , installation not yet start , error " c:/ is corrupted/unreadable." 
 
When i try to install ubuntu 9.04 , will failed somewhere at 75% , if not can finish installation , then when try to boot , error again . "the installer encountered an error copying files to the hard disk:
[Errno30] Read-only file system : '/target/boot/
 
vmlinuz-2.6.28-11-generic'

---

### Post by kerry_s on 2010-01-01
the best way to make a windows 7 usb is on a windows machine using the free trial of ultraiso:
[http://www.ezbsystems.com/ultraiso/](http://www.ezbsystems.com/ultraiso/)

you just select bootable-> write to disk, select your usb and you'll get a perfect installer usb from a iso file, i've done several from windows 2000 to windows 7 & many flavors of linux, it always works.

---

### Post by presence1960 on 2010-01-01
> **elaine81 said:**
> Nope , dun work , Win 7 stuck at "expanding files" , sometime , installation not yet start ,[B][U] error " c:/ is corrupted/unreadable." 
 [/U][/B]
When i try to install ubuntu 9.04 , will failed somewhere at 75% , if not can finish installation , then when try to boot , error again . "the installer encountered an error copying files to the hard disk:
[Errno30] Read-only file system : '/target/boot/
 
vmlinuz-2.6.28-11-generic'

we need to see what you have there on that machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

