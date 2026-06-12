---
title: "How to Install Tally ERP 9 client on LM17.2 Cinnamon 64 Bit"
date: 2015-07-25
forum: MINT
---

### Post by mayank1 on 2015-07-25
Dear Friends
Please help me installing and using Tally ERP 9 on my dual boot Laptop with win 8.1. My Tally Server is installed on different PC with window 7.
I am able to connect to tally in win 8.1 without problem ie just by giving server ip while installing tally erp 9.
But when I am trying to install tally in LM 17.2, I am getting error that path is unknown. I have tried to follow instructions given in this post [http://superuser.com/questions/695592/how-to-install-and-use-tally-erp-9-in-wine](http://superuser.com/questions/695592/how-to-install-and-use-tally-erp-9-in-wine) but not able to write correct details in mount.cifs command.

CODE: SELECT ALL
sudo mount.cifs //<your Tally server IP in tally.ini>/<Path to Data folder in tally server> -o /home/<your username>/.wine/dosdevices/c:/<path to your Data folder in tally.ini>


As per tally.ini file my details are as follows:
Tally Server IP : 192.168.1.1
Data folder path= \\HP-PC\D\Program Files\Tally ERP9\Data

Please guide me how to put above information in this command. 
I have little experience in commands as much you people have guided me.

I don't want to switch to windows to access tally every time.
Please help
I am posting this question here because Linux mint is also Ubuntu based distribution.

---

### Post by PaulW2U on 2015-07-25
*Thread moved to **MINT*** as you're not using an official Ubuntu flavour.

---

### Post by mayank1 on 2015-08-05
Hi
I am finally able to install and run Tally.ERP.9 in linux mint with following steps using wine
1. Mounting of windows share folder where tally is installed- at First I had mounted tally data folder on windows machine to mountpoint at /media/TallyData. You can check the same by using following command for any error: 
```
sudo mount.cifs <windows share folder path for tally data folder> /media/TallyData -o username=winuserid,password=winuserpass,iocharset=utf8,rw,nounix,file_mode=0777,dir_mode=0777
```
2. Entry in fstab: Once above step is successful then we can add a entry in fstab as follows
1. enter the below command:
```
gksu gedit /etc/fstab
```
2. add the following line at end of the file:
```
<windows share folder path for tally data folder> </home/mayank/.wine/drive_c/Program Files/Tally.ERP9/Data cifs username=winuserid,password=winuserpass,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlm, 0 0
```
3. Install tally with wine- Download the appropriate installation file from Tallysolutions.com site and run with wine. Install as client machine without changing any other parameter.
4. Creation of sym link: now create the symlink using ln command as given below
```
ln -s /media/TallyData “/home/linuxusername/.wine/drive_c/Program Files/Tally.ERP9/Data”
```
(I have used “” as ln command will give error due to space in our destination directory name( Program Files).)
5. Run the Tally.ERP9 and press F12 and Select Data Configuration. There change the path to C:\Tally.ERP9\Data\TallyData
6. Tally will ask for restart of tally and now you can access tally.erp 9 on windows machine.

Please guide me is there any other easy method to do the same?

---

