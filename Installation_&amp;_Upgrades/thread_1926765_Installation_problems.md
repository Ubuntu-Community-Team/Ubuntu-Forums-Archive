---
title: "Installation problems"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by JXR on 2012-02-16
Trying to install Ubuntu 10.04 on a Compac Pressario.

The program will run off CD but when I try and install it (instructing it to reformat the disk as part of the process) the following occurs:

 (15% progress bar)
  input/output error during write on /dev/sda                                      [Retry]  
  Error fsyncing/closing/dev/sda input/output error
  

(5%)
  Creating ext4 file system for / in partition #`1 of SCSI1 (0,0,0)  (sda)  
  The ext4 file system creation #1 of SCSI1 (0,0,0) (sda) failed   [OK]
  Vbi-migrationassistant failed with exit code 141. Further information may be found in /var/bg/syslog                                                                [Continue Anyway]
  

Retried a number of times all with the same result. 

What am I doing wrong or is there any way to complete the installation?

Thanks

---

### Post by uRock on 2012-02-16
Hello and welcome to the forums,

Have you tested the disk by selecting the CHeck Disk funtion when it first starts booting?

What is your system's specs?

---

### Post by JXR on 2012-02-16
I assume by the disk you mean the CD?  The disk came with a book Ubuntu for Non-Geeks. I don’t remember there being an option to check the CD. 
   
  (I’d actually downloaded, and unzipped the program from the web—compared the contents of the two disks and aside from creation dates were identical. But when my disk didn’t do anything [Got the message “NDVIR missing, press Cntl Alt Delete to restart”], I managed to find the book and try its CD.)
   
  I suspect the writer is coming up against a bad spot on the hard disk, but I’m not knowledgeable enough to go in and repartition the drive to avoid bad sectors. Is this a possible way around the problem?
   
  As to System specs, the computer used to run XP Pro but now is not booting.

---

### Post by uRock on 2012-02-17
If ```
NDVIR missing, press Cntl Alt Delete to restart
```is the message you are getting, then you aren't booting from the disk. You should get a purple screen, then when the screen with the little keyboard shows up, hit any key, then select you language, then select to Check Disk for Defects.

---

### Post by JXR on 2012-02-17
No I tried the installation with two different CDs.
   
  CD #1: Contains Ubuntu (downloaded/unzipped) from the Ubuntu site. Doesn&#8217;t work. When I place it in the CD drive and run the computer it skips the CD autoload and eventually gets to the &#8220;NDVIR missing&#8230;&#8221; response, indicating the computer insists on booting from the internal hard drive. Because this didn&#8217;t work I went on to CD#2.
   
  CD #2: Appears identical to CD #1 (at least from a root) and obtained from the book Ubuntu for Non-Geeks . Automatically boots to a screen that gives two options [Try Ubuntu 10.04 LTS] and [Install Ubuntu 10.04 LTS]. Either option works (the former provides an interactive splashscreen displaying an example Ubuntu install; the latter actually tries to do the install)&#8212;indicating the computer is booting from the CD. However, at no point in the process is there an option to &#8220;check the disk&#8221;. When the installer gets to the part where it&#8217;s asking you if you want to reformat the disk and insert Linux it prints bars indicating disk space already appropriated. So it must be able to read the disk.
   
  (Latest annoyance: In giving Ubuntu all the time it needed to try and install something must have damaged the screen. Now there is a bright green vertical line about an inch from the left screenedge&#8212;that does not go away. Argguh!)

---

### Post by mastablasta on 2012-02-17
> **JXR said:**
> [FONT=&quot]**No I tried the installation with two different CDs.**[/FONT]

**[FONT=&quot]CD #1: [/FONT]**[FONT=&quot]**Contains Ubuntu (downloaded/unzipped) from the Ubuntu site. Doesn’t work. When I place it in the CD drive and run the computer it skips the CD autoload and eventually gets to the “NDVIR missing…” response, indicating the computer insists on booting from the internal hard drive. *Because this didn’t work I went on to CD#2.***[/FONT]

 
Wrong! You need to burn the image to a CD (or oyu can stick it on USB using for example unetbootin). there is no "unzipping" to do. that's why it didn't work. becuase CD needs to have a bootflag.
**** 
***here is how you do it: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)***
**** 
> 

**[FONT=&quot]CD #2[/FONT]**[FONT=&quot]**: Appears identical to CD #1 (at least from a root) and obtained from the book _Ubuntu for Non-Geeks_ . Automatically boots to a screen that gives two options [Try Ubuntu 10.04 LTS] and [Install Ubuntu 10.04 LTS]. Either option works (the former provides an interactive splashscreen displaying an example Ubuntu install; the latter actually tries to do the install)—indicating the computer is booting from the CD. However, at no point in the process is there an option to “check the disk”. When the installer gets to the part where it’s asking you if you want to reformat the disk and insert Linux it prints bars indicating disk space already appropriated. So it must be able to read the disk.**[/FONT]

Not sure whyat they did and which version they have but the check disk is only to verify the burned CD. clicking on try it should bring you into the operating system that loads itself to ram. if you can't get to the oparating sytsem then you might need to use one of the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
Another option is to use alternate cd for install. 
 
BTW what are your system specs?
 
 
 
> 

[FONT=&quot]**(Latest annoyance: In giving Ubuntu all the time it needed to try and install something must have damaged the screen. Now there is a bright green vertical line about an inch from the left screenedge—that does not go away. Argguh!)**[/FONT]
 
Ubuntu didn't do that. perhaps you need to move your screen on th emonitor a bit to the left?

---

### Post by uRock on 2012-02-17
When you boot into the live (try ubuntu) mode does it boot all the way to a working desktop? If yes, then go in the menus to System> Administration> Disk Utility and test the hard drive.

We need to know about your system's hardware specs. 32 or 64 bit? nVidia or Intel graphics. At a minimum, knowing what model it is would be helpful, ie Dell Optiplex 2980.

---

### Post by JXR on 2012-02-17
You guys are all too helpful!!  (I’m not conversant with “Quick Reply” so I’ll address you both in this Reply)
   
  [SIZE=3]**Mastablasta**[/SIZE]
   
  ** CD#1**: The reason I’d unzipped the files (and thought I’d done the right thing when the disk looked so like the book version (CD#2) was because originally I’d just put the .iso file on, and gotten the NDVIR report. I unzipped the file burned a new CD and continued to get the NDVIR report. (both indicating the computer’d bypassed the CD and tried to boot from the hard drive).
   
  I reburned a new CD with the downloaded file **ubuntu-10.04.3-desktop-i386.iso** and tried it again. This time no NDVIR message (I think all my attempts to write Linux on the computer have somehow overwritten the call to NDVIR); just a blinking cursor on a black screen.
   
  I’d really like the downloaded 704,226 Kb file to perform the install. [SIZE=2]
Is there something I’m not doing that I need to do to signal to the computer that **ubuntu-10.04.3-desktop-i386.iso** is an auto start executable?[/SIZE]
   
  **The one pixel green vertical line** 1” away from the left edge of the screen. I don’t think it’s Ubuntu’s fault and I can live with it.  Probably a screen fault waiting to happen. It didn’t come at the right time though. This computer is my Linux experience testbed. I don’t mind a crease in the sheets.
   
  **[SIZE=3]uRock[/SIZE]**
   
  When I boot into the live mode it boots all the way to the working desktop. I thought it was just for display, but, yes System Administration/Disk Utility works! Since this is the only approach that is getting somewhere I’m going with it for the time being (and then hoping to upgrade after Ubuntu has commandeered the computer).
   
  System Administration/Disk Utility: 
It sees: 
     DRIVE: 18 Gb ATAIBM-DARA-218000  Firmware: GL6OA5AO Partitioning: Master Boot Record   Device: /dev/sda
     VOLUME: Linux (0x83)  Device: /dev/sda1
   
  [FONT=Calibri]-          [/FONT]I’m tempted to “Format Drive” (hoping it’ll detect and segregate bad sectors) but took the safe course and just ran “Benchmark”
  [FONT=&quot]o   [/FONT]**Read Only Benchmark**: Error benchmarking drive: An error occurred while performing an operation on “18 Gb Hard Drive” (ATAIBM-DARA-218000 ) : The operation failed    Details: Error benchmarking: helper extend with exit code 1: Device /dev/sda is too slow to benchmark
   
  Other Computer specs: Compac Presario 1800T; 32 bit (I assume Intel graphics).

[SIZE=2]What should I do now?[/SIZE]

---

### Post by uRock on 2012-02-17
I am tempted to say that it needs a new HDD, but I recommend waiting for someone more hardware savvy to advise on the output of the error.

---

### Post by JXR on 2012-02-18
I followed your instructions&#8230;used InfraRecorder&#8230;3 CDs later (48x, 32x, 16x)&#8230;had the iso properly written to disk&#8230;inserted it into the Compac&#8230;and&#8230;got exactly the same screen as the CD from the ...non-Geeks book&#8230;instructed it to install Ubuntu&#8230;
    
   Three hours later it&#8217;s still chugging away, progress bar at 5%, the screen cheerfully informing me &#8220;The installation will finish soon. We hope you will enjoy Ubuntu.&#8221; 
    
   Suggestions?

---

### Post by JXR on 2012-02-18
Decided to try reformatting the 18 Gb drive (from Ubuntu) with the following results:
  Error formatting drive…The operation failed
  Details: Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on dev/sda: Input/output error.

---

