---
title: "Installation Error: Permission Denied"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by sycoskater16 on 2010-11-23
Hello all,

I recently re-formatted my computer due to Viral problems, and have been in need of a new OS. My computer is completely blank and freshly cleaned and I'd just hate to ruin it with more Microsoft crap. So all in all, Linux is what I want to try, but unfortunately I know nothing of Linux or how it works :(.

So here I am, A completely newb to computing, asking the forums for advice. I have the Ubuntu 10.10 rar file sitting on my desktop, ready to be unzipped.

Now I've already looked into burning me an ISO file onto a CD, and also I've looked into putting it onto a USB drive and installing it that way. The only problem is I can't locate the ISO file that I need in order to install the OS! I've already tried unzipping the RAR file, but I still see no OS. I ran WUBI.exe, only to have it crap out at 60% while downloading something (the ISO file mebe?). I've tried deleting everything and re-DLing the whole rar file, but same error.

So im really stuck on how to get Ubuntu on a PC that has no OS already. I've done my research on alot of different forums, but its all so confusing that I don't know what im doing right or wrong.

The PC im trying to get Ubuntu on is able to read CDs, and boot from USB. I have a SanDisk 16gig Cruzer and a stack full of CDs at my disposal in order to get this going, so ANY help is appreciated.

Thanks again,
Cheers!

(P.S) Here is that log file. Permission Denied is what I see as an error.. Again; sorry for my lack of knowledge:

DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


11-23 10:23 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
11-23 10:23 DEBUG  TaskList: ### Finished download
11-23 10:23 ERROR  TaskList: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-i386.iso'
11-23 10:23 DEBUG  TaskList: # Cancelling tasklist
11-23 10:23 ERROR  root: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'G:\\ubuntu\\install\\ubuntu-10.10-desktop-i386.iso'
11-23 10:23 DEBUG  TaskList: # Finished tasklist

---

### Post by drdos2006 on 2010-11-23
Hi 
My personal opinion would be to download version 10.4 Long Term Support rather than 10.10. I had too many unreliable problems with 10.10 on my hardware.
Burn the downloaded ISO to a CD. Boot from the CD as it will let you test USB video etc before installing. ( It will be a LiveCD ).
USB is usually FAT32 and not Linux ext3 or ext4 so that may be a problem.
If you need to dual boot, then the livecd has a program called gparted which can set up a Windows partition, a Ubuntu partition, a Data partition and a swap partition. Install Windows first, then Ubuntu looks after everything else. Later Windows OS than XP have a tendency to overwrite all other OS files and is not as well behaved as Ubuntu.
 
regards

---

### Post by tommcd on 2010-11-23
> **sycoskater16 said:**
>  I have the Ubuntu 10.10 rar file sitting on my desktop, ready to be unzipped.

The Ubuntu 10.10 rar file? Where did you get this? I have been using Ubuntu for 5+ years, and I have never used a Ubuntu rar file, or even heard of one.
Get the Ubuntu iso image from Ubuntu.com: [http://www.ubuntu.com/](http://www.ubuntu.com/)
See this on buring the iso image to a CD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
If you are burning the CD from Windows, use *Iso Recorder* or *Infra Recorder*. And be sure to burn the CD at the slowest possible speed. 
Set your computer's BIOS to boot from the CDROM drive as the first boot device so you can boot from the CD.
When you boot from the CD, first choose the option "*Check CD for Defects*" and let that run. If it reports no errors then the CD is good and can be used to install Ubuntu.
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
Here is a great site for getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

And welcome to the Ubuntu forums!

---

