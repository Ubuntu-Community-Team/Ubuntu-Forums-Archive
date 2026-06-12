---
title: "1) Invalid disc image 2) wubi woes"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by jez_24 on 2011-07-04
Hi,
 
I've tried to search for similar problems/solutions to mine but I'm just not at the level required to understand the finer points of most other posts. So I apologise if this problem has already been answered...
 
I downloaded ubuntu-11.04-desktop-i386.iso, I'm running windows 7 professional and I've partitioned my hard drive to create a new volume that I want to run ubuntu on, while keeping windows on the C drive.
 
First problem; clicking the .iso file opened windows disc image burner. 'The selected disc image file isn't valid'. Found out about the hashes and checked the md5sum values- totally different. 
d9e78b2322e02628293911764ed75a34
8b1085bed498b82ef1485ef19074c281
 
Trying to find out what to do about that but first...
 
I tried opening it with winrar and extracted the files, found wubi and ran that. I chose the newly created volume. 
 
Second problem; after the installer has downloaded its stuff it hits a wall and doesn't finish. Error message with 'permission denied' in it and the location of a log file to find further information. I decided to run it as an administrator (W7 and its bloody permissions!) but the same thing happened again. Here is the log info from where it looks like there was trouble up till the termination;
 
07-04 23:03 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>
in task download
07-04 23:03 DEBUG TaskList: ### Finished download
07-04 23:03 ERROR TaskList: [Errno 13] Permission denied: u'F:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'F:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
07-04 23:03 DEBUG TaskList: # Cancelling tasklist
07-04 23:03 DEBUG TaskList: # Finished tasklist
07-04 23:03 ERROR root: [Errno 13] Permission denied: u'F:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 57, in run
File "\lib\wubi\application.py", line 131, in select_task
File "\lib\wubi\application.py", line 157, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'F:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
 
Sooo...what do I do? Any help will be greatly appreciated but you'll probably need to be patient with me lol

---

### Post by Rubi1200 on 2011-07-04
Hi and welcome to the forums :-)

If the hashes don't match you need to download the ISO image again perhaps from another source such as a torrent (they are pretty good at making sure the hashes match).

Burn to CD at the lowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

To install Wubi (hopefully without errors) place the downloaded Desktop ISO and wubi.exe in the same folder and then run the executable. Make sure the versions match.

Another point, if you have dynamic disks in Windows (you can check via the Disk Management utility) then this is probably not a good idea to try and install Ubuntu (Wubi or otherwise) since they do not play well together.

Finally, if you left a partition unformatted, I would format it to NTFS and then try the install.

---

