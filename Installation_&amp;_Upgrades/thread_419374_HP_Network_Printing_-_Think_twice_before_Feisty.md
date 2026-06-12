---
title: "HP Network Printing - Think twice before Feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by tagra123 on 2007-04-22
First:  I held off upgrading to Edgy and stayed with Dapper. Yesterday, I downloaded and installed Feisty. Everything I wanted to install is now installed.  

I preserved my home directory, but I may try a new install just in case something remaining there may have caused the problem.


Super -- Feisty installs easily. 

Samba is working fine.


Now for the problem

I have a HP DeskJet-3940.


The printer will print from the the text editor, firefox, etc on the local machine just fine., but it will not print a test page from gnome-cups-manager and it will not print over the network -- just blank pages. It will print a testpage from [http://localhost:631](http://localhost:631) , but thats about it.

I am disgusted with cups. In my opinion CUPS hasn't work right since Breezy. I use  Ubuntu for business and yes even in 2007 some people want hard copies of their documents. 


I'd like to stick with Feisty but I need to print. 

Anyone have any ideas.  

I'm going to backup my current Feisty install and restore my dapper backups.  


When the printer is on the Dapper machine get ipp printing doesn' , but I can print in Dapper using samba.


I haven't been able to use ipp or http since Breezy -- what a shame.


Am I missing something?

---

### Post by tagra123 on 2007-04-23
Anyone know how to make this work?

---

### Post by jmagsho on 2007-04-23
Tagra,

I'm in the same boat (well, except for using Ubuntu in my business that is -- although up until now I would have seriously considered it).    My Photosmart 3210 is non-functional since upgrading to Edgy and I mistakenly thought that it might have been corrected in Feisty.   I too was mistaken, and yes it is a shame.   Looks like I'll be restoring my Dapper image later today...

---

### Post by JohnsonMR on 2007-04-23
I don't have all the details with me but you need to create a second printing queue on the system that controls the printer.  That queue will need to use a PS driver (as I recall) for the printer to work.  This new queue will point to the original printer.  Send all your prints to that new queue.

There are several messages on this board about this problem from about six months ago.  Once I get back home I might be able to find the details, or perhaps you will have found it by then.  In any case, It fixed my CUPS and HP printer problems...

---

### Post by jmagsho on 2007-04-23
Ok, I think I figured it out.  I added my user to the shadow group, and also installed the 'hpoj' driver.   Followed the setup prompts when installing hpoj from a terminal window and deleted the existing printer, and then recreated it using JetDirect setup (socket://ip address:9100).     The thing seems to be working like a champ now.   I also took heed of the instructions and edited dll.conf for sane so I could get scanning working too.   Haven't tested just yet, but I'm hopeful!

---

### Post by tagra123 on 2007-04-24
Thanks jmagsho -- I'll give it a try on one of the other PC's Read on

JohnsonMR 

I installed Debian Etch yesterday.  I have everything working just like ubuntu did -- except printing actually works.

The only thing I've been looking for and havent been able to find is  MythTv.18 debs for etch. I'm sure they will turn up sooner or later.

What bugs me with the printing is that on the Debian machine I shared the printer with samba and this is the result

#1 Debian Machine with printer -- Printer Works
#2 Machines with windows printing to #1 Works
#3 Machine with Feisty printing to #1 will make the printer print a blank page just as before.

It seems like it is not sending text to the printer. I can here the head moving back and forth and the paper but tada, a blank page.

Printing via IPP from Feisty to Feisty didnt work. Printing via samba to Feisty didnt work.

By the way Java wont print either.  

Ubuntu is a little easer to set up, but debian wasn't that hard and I'd rather spend 2 hours getting everything installed and work that 2 hour and still the same result.

A how to print in Feisty is needed.


<RANT>
I bet with paid support CUPS can work. 

Although there may be some problems with CUPS itself, Ubuntu has managed (for security, I guess) to make it so secure that it wont even print. Good job. Way to go!!!
</RANT>

---

### Post by tagra123 on 2007-04-25
Just another thought.

Could it be that a driver is need or missing. The ppd is installed but still nothing but blank pages over the network when using Feisty.  

If I could find version .18 of Mythfrontend for debian and I would just convert the other machine to etch and be done with the printing problems.

Next test will be to install debian in a VM and see if it can print to the debian machine. I think it should. This will at least let me know if it is ubuntu problem which I believe it is.

---

### Post by tagra123 on 2007-05-04
HOW TO SHARE PRINTERS -- THE UGLY WAY

This could also be called  A WAY TO DEAL WITH UBUNTUs IMPLEMENTATION OF PRINTING

This will work with samba  -- although printing from windows to ubuntu dapper seems to work just fine if setup as samba.  Fiesty to Dapper printing doesn't play nice.

I wanted to create a setup I knew should work regardless of updates and if the simple hello test works on the local machine printing should work on any of the other machines.

Its a very ugly hack but simple to setup to work this way:

This example will use nfs but samba could also be used to share the files.

Setup the printer on the computer that has the printer attached as you normally would and set it as default.

Test it to see if its working.
```

echo "hello" >test
lpr test

```

If it prints then continue with the next steps.


***_#1 ON THE MACHINE WITH THE PRINTER TO SHARE  (THE SERVER)_***

Install NFS
```
sudo apt-get install nfs-kernel-server
```

Create a "Spool" -- this is where the print files will be stored.

```
sudo mkdir /printing
sudo chmod 777 /printing
```

next

```
gksudo gedit /usr/sbin/fakenetprint
```

Add this to the text file
```

#!/bin/sh
# This script was written as a hack to allow networking printing between dapper and feisty

#To SET UP the host with -- computer with the printer
# 1 Create a directory named printing sudo mkdir /printing
# 2 Grant it permission sudo chmod 777 /printing
# 3 Share the /printing folder using NFS or SAMBA -- I prefer NFS
# 4 Add A Cronjob I set mine to check once a minute (This needs a measure to keep cron from running if the previous instance hasn't stopped yet

#To set up the Client (the computer printing to the computer with the printer)
#1 Create a directory named remoteprinter  sudo mkdir /remoteprinter
#2 Change permissions  sudo chmod 777 /remoteprinting
#3 Edit fstab to mount the share from the host
# it should look something like this for nfs  
# someservername:/printing /remoteprinting   nfs  rw  0  0
# or if using an ip (your numbers will be diffferent
# 192.168.1.2:/printing /remoteprinting nfs  rw  0  0 
# when finished editing /etc/fstab save and close the editor
# sudo mount -a
# To use the printer print to a postcript file and save the file in /remoteprinting
# the script on the computer with the printer connected will take care of the rest.
# TOM GRAHAM 2007 HACK To PRINT USING UBUNTU


TARGETPATH="/printing"
FILESIZE_A="0"
FILESIZE_B="0"

for FILENAME  in `ls -dXr $TARGETPATH/*`;do
  
  let "FILESIZE_A=$(stat -c%s "$FILENAME")" 
  sleep 3
  let "FILESIZE_B=$(stat -c%s "$FILENAME")"
  if [ $FILESIZE_A == $FILESIZE_B ]; then
          echo "Size of files are same" 
          #line below could also be like lpr -P DeskJet-3920 $FILENAME
          lpr $FILENAME
          rm $FILENAME
        
     else
           echo " Size of files are different"
         
     fi
 done

```

Save the file and close the editor.

Change permission to allow execution.
```
sudo chmod +x /usr/sbin/fakenetprint
```

Create a cronjob to run the script (this is our fake scheduler)
```
gksudo gedit /etc/crontab
```

Add the following lines to the very end of the file
```
#FAKENETPRINT (Simple way to share network printer)
* * * * * yourusername /usr/sbin/fakenetprint

```

Next edit the /etc/exports file.  This is using NFS for file sharing. If you are using samba for file sharing edit the necessary in smb.conf.

```
gksudo gedit /etc/exports
```
Add the following line to the end
```
/printing  192.168.1.0/255.255.255.0(rw)
```
(My gateway is 192.168.1.1 -- to share to the entire network -- use the line above. Your numbers may be different. Read up on nfs if you don't understand the line above.

Save the file and exit the editor.

Restart nfs:
```
sudo /etc/init.d/nfs-kernel-server restart
```




That's it for the computer that has the printer attached

*_/B]#2 On the Client computer -- The one without a printer*_[/B]


Install NFS
```
sudo apt-get install nfs-kernel-server
```

Create a "Spool" for remote printing -- this is where the print files will be stored. this file could also be create in the home directory or anywhere else.

Next, setup the NFS to automount when booting the computer.

```
gksudo gedit /etc/fstab
```



```
sudo mkdir /remoteprinting
sudo chmod 777 /remoteprinting
```

Now lest suppose the ip address of your computer with the printer is 192.168.1.5 (your IP will be different)

```
gksudo gedit /etc/fstab
```

Add the following line to the very end of the file.
```
192.168.1.5:/printing /remoteprinting   nfs   rw    0       0
```

Save and exit the editor.

Mount the share (it will auto mount from now on)

```


sudo mount -a
```

THATS IT.

To Print on the client machine to the remote printer 

Click on print and select PS/Postcript Printer
Select print to file.
the path should be /remoteprinting/someoutputfile

Depending on the timing of the cron job the printer should begin printing within a minute.


HA AH UBUNTU -- No matter how hard you try you can't keep me from printing over a network.


Any additions or improvement s to this are welcome.

---

### Post by tagra123 on 2007-05-04
Just a request for next release.  Can somone please come up with something that is backwards compatible and actually works for printing.


Printing, in my opinion has not even been close to acceptable since Breezy!!!

---

