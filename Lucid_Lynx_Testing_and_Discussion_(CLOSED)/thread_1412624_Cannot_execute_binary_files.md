---
title: "Cannot execute binary files"
date: 2010-02-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sinurge on 2010-02-21
I cannot run the internet connection utility that comes from my isp. Every time i try to run the same i get an error, i have triple boot with jaunty+mint helena + lucid. It works perfectly fine with those it just does no in lucid below is the ls listing and error 

below is the output from the lucid lynx 

zack@zack-lucidlynx:~/Documents/crclient$ ls -l
total 32
-rwxr-xr-x 1 zack zack 29580 2010-02-21 19:42 crclient
zack@zack-lucidlynx:~/Documents/crclient$ ./crclient -s
bash: ./crclient: No such file or directory
zack@zack-lucidlynx:~/Documents/crclient$ 


below is the output from the jaunty

zack@dsotm:~$ cd Documents/crclient/
zack@dsotm:~/Documents/crclient$ ./crclient -u th_zack5
zack@dsotm:~/Documents/crclient$ 
./crclient:user 'th_zack5' successfully logged in to server '10.23.11.1'

:confused::confused::confused:

brian@dsotm:~/Documents/crclient$

---

### Post by ronacc on 2010-02-21
check the permissions on the file to make sure it is executable and that you have execute permission , otherwise use sudo .

---

### Post by sinurge on 2010-02-21
thanks, but i did check that with the permissions on the jaunty setup as well no issues, i copied the same files to mint-helena and worked there as well. 

what i have done is copied the binary from jaunty to a usb stick so i just can copy it directly to the distro am running

---

### Post by autark on 2010-02-21
If I remember correctly, that kind of phenomenon can occur if you are trying to execute something from a device that is mounted without exec permissions. Check the output of the mount command and watch for "noexec".

---

### Post by Salane on 2010-02-21
Same problem. It looks like a deliberate dumming down on the ablility of running a user program, unless it really is a bug.
pwd
/home/user/Downloads/w_scan-20091230

sudo /home/user/Downloads/w_scan-20091230/w_scan -fa -A2 -X -cUS > channels.conf
sudo: unable to execute /home/user/Downloads/w_scan-20091230/w_scan: No such file or directory

user@slklinux:~/Downloads/w_scan-20091230$ ls -l /home/user/Downloads/w_scan-20091230/w_scan
-rwxr-xr-x 1 user user 317942 Dec 30 13:13 /home/user/Downloads/w_scan-20091230/w_scan 

I am getting a no such file or directory when obviously there is a file and it has permissions to be executed.

---

### Post by mdurham on 2010-02-21
> what i have done is copied the binary from jaunty to a usb stick so i just can copy it directly to the distro am running 
What format is the USB stick? If it's fat32 you will loose any permissions as it doesn't support them.

---

### Post by alexmurray on 2010-02-21
Sounds like you're trying to run a precompiled 32-bit application on a 64-bit installed - try installing ia32-libs and see if it works after that.

---

### Post by sinurge on 2010-02-22
> **alexmurray said:**
> Sounds like you're trying to run a precompiled 32-bit application on a 64-bit installed - try installing ia32-libs and see if it works after that.
Thanks!

@[mdurham]("http://ubuntuforums.org/member.php?u=48410") yes, if it lost all the permissions, when i copied to my new home/Documents directory, it would have inherited those permissions wouldn't it.? 

[@alexmurray]("http://ubuntuforums.org/member.php?u=748826") will do that, my helena is also x64 but it does not seem to have any issue with it. The binary allows me to connect to the internet hence cannot connect to the internet to check teh ia320libs

---

### Post by sinurge on 2010-02-23
Well! Thanks everyone. ia32-libs while checking was a huge 607 mb download. I might have got this wrong. So did the next best thing downloaded the 32bit iso for lucid lynx and did it again and i works.

---

