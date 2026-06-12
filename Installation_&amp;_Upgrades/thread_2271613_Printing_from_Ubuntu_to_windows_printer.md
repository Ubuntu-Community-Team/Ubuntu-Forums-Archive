---
title: "Printing from Ubuntu to windows printer"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by Peter_Williams on 2015-03-31
I have a Deskjet attached (USB) to a Windows 7 desktop.
I also have an oldish Toshiba laptop onto which I have recently installed Ubuntu
I have installed Samba and CUPS
I have managed to get file sharing across my network but failed to get access to my printer over the network
If I attach the printer directly to the laptop - it works fine (just printed a CUPS test page)
When I try over the network - when connected to the windows machine - I fail

The printer appears OK but I get a message when I look at the printer status 
"Stopped - Rendering Completed"

I have the following code in the smb.conf file

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
    # to allow user 'guest account' to print.
;    guest ok = no
;    writable = no
    printable = yes
    create mode = 0700
    write list = @adm root Peter

Any help appreciated

---

### Post by SeijiSensei on 2015-03-31
Samba is designed to let Linux machines act as file and print servers for Windows clients.  I presume your printer is attached to the Windows machine with sharing enabled.  If so, CUPS can connect to it directly. On the Ubuntu machine, point a browser at [http://localhost:631](http://localhost:631).  You'll see the CUPS manager.  Click on "Adding Printers and Classes."  You can try the "Find New Printers" button, and if that doesn't work, choose "Add Printer".  Enter your own username and password when prompted, then choose "Windows Printer via SAMBA" from the list and follow the steps involved.

---

### Post by Peter_Williams on 2015-03-31
I've already done most of above.
Have used CUPS
[connected via http://localhost:631]("http://api.recomme.me/widgets/PromoManager/HJjOZY6KF6lVhsJNEoLm.html?usa=true&countdown=false&ptID=229&cID=1015&rt=linkreplace&ascID=2356141&mid=34EBF91594B7894D1C09D4F39BBFE6BE&pid=18&rv=45&pmUrl=http%3A%2F%2Flocalhost%3A631%2F")
Added printer HP_on_Desktop

see images attached

[Image2]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print02.jpg")
[Image3]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print03.jpg")

I don't recollect "Windows Printer via Samba"

---

### Post by SeijiSensei on 2015-03-31
Remove the HP from the printer list and install it again from the web-based interface.  Right now it's configured to be local to the Ubuntu machine rather than using a network connection.

---

### Post by Peter_Williams on 2015-04-01
I have done what I understand you suggest - but suspect I have something wrong again.
I seem to have the same problem and again shown in the 2 attached screenshots

[ImageA]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print11.jpg")
[ImageB]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print10.jpg")

I have tried to install 
Device URL as socket://peter = user on Ubuntu
and 
Device URL as socket://ubuntu name of laptop computer as seen on network
and
Device URL as socket://USER-PC name of desktop computer as seen on network

is this the correct way to complete this entry for Device URL ?

---

### Post by SeijiSensei on 2015-04-02
If the printer is connected to a Windows machine and being shared, then I use "smb://servername/printername" as the URL if using the "Windows Printer via Samba" option.

---

### Post by Peter_Williams on 2015-04-02
Hi and thanks again

Seems like a different problem

[Image1]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print21.jpg")
[Image2]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print22.jpg")

I am not aware of a password on the PC - sort of looks like the NT refers to the windows machine

---

### Post by SeijiSensei on 2015-04-02
If you browse your network from Windows, what hostname do you see for the print server?  If you double click that icon, what is the printer name it reports?  Use those hostname and printername values in the smb://hostname/printername URL.

---

### Post by Peter_Williams on 2015-04-03
Hi and thanks again

Image3 shows the view from Windows and Image1 shows printer config on Ubuntu.

i.e. smb://HOMEGROUP/UBUNTU/HP_Deskjet_F2480
Also the printer is 'shared' as per Image4

[Image1]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print21.jpg")
[Image2]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print22.jpg")
[Image3]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print23.jpg")
[Image4]("http://mybetterlife.co.uk/My_Images/Ubuntu_Print24.jpg")

Tried most combinations and the CUPs info doesn't help me identify the problem

---

### Post by SeijiSensei on 2015-04-03
Image 3 shows the computer's name is UBUNTU and the printer's name is HP_Deskjet_F2480, making the correct URL
```
smb://ubuntu/HP_Deskjet_F2480
```
I'm even more confused that this machine is called UBUNTU!  I thought you said the printer was connected to a Windows computer?

---

### Post by Peter_Williams on 2015-04-03
> **SeijiSensei said:**
> Image 3 shows the computer's name is UBUNTU and the printer's name is HP_Deskjet_F2480, making the correct URL
```
smb://ubuntu/HP_Deskjet_F2480
```
I'm even more confused that this machine is called UBUNTU!  I thought you said the printer was connected to a Windows computer?

Hi

The printer is connected to the Windows laptop but I assume the 'server' is created by Samba on the Ubuntu machine. I'll try switching the names

---

### Post by Peter_Williams on 2015-04-06
> **Peter_Williams said:**
> Hi

The printer is connected to the Windows laptop but I assume the 'server' is created by Samba on the Ubuntu machine. I'll try switching the names

Somehow I now have a system that appears to file share and print share.  Not exactly sure what I have done - just keep trying the combinations available in SAMBA / CUPS

Thanks for your help

---

