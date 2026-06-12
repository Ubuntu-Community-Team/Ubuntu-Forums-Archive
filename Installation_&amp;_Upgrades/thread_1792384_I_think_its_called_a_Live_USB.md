---
title: "I think its called a Live USB?"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by zoi0sooB on 2011-06-28
Hey,

Im hoping to install Ubuntu 11.04 onto my USB... (1 gb... all i want it for is to do virus scans and stuff for my windows computers....) The thing is, I did the Startup disk thing.... But every time i boot off the usb it says "Try or install"

I click try... I make a file on the desktop... then i reboot and its gone!

Why is this happening, and how do i get the files to save?

Im pretty sure this question has been asked 1000 times before.... but i cant find any previous threads...

If somone could, either point me in the right direction or tell me what to do?

---

### Post by westie457 on 2011-06-28
HI you need to create a persistence file.
When using Startup Disc Creator to create a LiveUSB near the bottom of the window is an option to reserve some space on the USB stick to store any extra applications that you install and any pics, docs and such like that you download or transfer.

The persistence file can be any size you want upto the maximum space available after the .ISO file has been created on the stick

---

### Post by zoi0sooB on 2011-06-28
> **westie457 said:**
> HI you need to create a persistence file.
When using Startup Disc Creator to create a LiveUSB near the bottom of the window is an option to reserve some space on the USB stick to store any extra applications that you install and any pics, docs and such like that you download or transfer.

The persistence file can be any size you want upto the maximum space available after the .ISO file has been created on the stick

I read about that but in my ignorance i ignored it... Thank you very much for answering my silly question...

Ill try that now.

PS. What will the default superuser password be?

---

### Post by nzjethro on 2011-06-28
The live CD uses the default profile "ubuntu@ubuntu", for which no password is required. Just type

```
sudo <command>
```

---

### Post by zoi0sooB on 2011-06-28
The little thing you were talking about is blanked out when i go to make a startup disk...

But it works on my 32gb USB.....


GAHHHHH!!!!

Is that because of there being plenty of space free after it installs?

I really need this to go on my 1 gb... not my 32 D=

---

### Post by westie457 on 2011-06-28
You need to erase the usb stick to free up the space

---

### Post by zoi0sooB on 2011-06-28
> **westie457 said:**
> You need to erase the usb stick to free up the space
ive done that

---

### Post by westie457 on 2011-06-28
Under the one you have high-lighted there will be another 'drive'. Use that one. At the moment you actually are trying to use the MBR of the usb stick. The main part of the stick is there, you can see the top 2 or 3 millimetres of it's name.

---

### Post by zoi0sooB on 2011-06-28
> **westie457 said:**
> Under the one you have high-lighted there will be another 'drive'. Use that one. At the moment you actually are trying to use the MBR of the usb stick. The main part of the stick is there, you can see the top 2 or 3 millimetres of it's name.
What? I dont understand?

The one under it is my 32 gb... I want to install it to my 1 GB...

---

### Post by mastablasta on 2011-06-28
he means that the drive you are supposed to install to is under /dev/sdb1 on your pic
 
if you have windows you might find this easier to use (from windows): [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
 
select the amount of persistance you want in step 3 i think.
 
Threre salso another easy one called Unetbootin.
 
BTW there are special distributions of Linux for file recovery, disk recovery and virus scanning.

---

### Post by westie457 on 2011-06-28
> **famematt said:**
> What? I dont understand?

The one under it is my 32 gb... I want to install it to my 1 GB...

Temporarily remove the 32 GB one.
If you click (again) on erase disk to Format it you will then get an option to open it and use the new file system. Then you will have all options open to you.

At the moment if you go ahead you will be creating basically a LiveCD with a closed file system. Which will be the same as any installion disc.

I am having trouble attaching a screenshot at the moment so cannot show exactly what I mean so I will try to explain.

At the moment on my Startup Disc Creator window is listed under Disk to use

          /dev/sdb      secure digital drive    958MB 
          /dev/sdb1     NEW VOLUME              957.6MB   297.8MB
       
The /dev/sdb  is the whole drive as one partition.

The /dev/sdb1 is the new file system after formatting. The 297.8MB is how much space is available for the persistence file.

Just worked out how attach pictures. The one attached shows what I mean.

---

