---
title: "Copying / Installing packages"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by rverwey on 2005-11-15
Hi all,

After I was totally fed up of all problems with XP, I've been trying to install Ubuntu these days. These are my first steps in a non-Windows environment, any help is very appreciated in getting Linux run on the computer. 

While installing Ubuntu on my HP laptop, I received an error message that the "copying the packages failed". It said that either the hard disk was full and additionally the suggestion to burn the CD on a lower burn speed was send.

I'm almost sure that the hard drive is not full, since I chose the 2nd option in the menu (erase hard disk - created 2 partitions, one swap of 1.3 GB and another for the rest of 38.7 GB). Therefore, I burnt the CD another time on the lowest possible speed and once again in the installation procedure it gave me the same error. I also downloaded Kubunti, which also presented the same error.

Contrary to Ubunti, with the Kubunti package I have been able to finish the installation procedure, and the computer rebooted successfully. However, after rebooting, Kubunti continued the installation with installing the packages. In this stage the computer keeps on stating "preparing for installation... 0%", without any change (for over 30 minutes yet)

I do not know what I can do in order to make the software packages work. 

Any help is very much appreciated.

Thanks in advance!

Roy

---

### Post by adwait on 2005-11-15
Ok first off........its KubuntU and UbuntU.

As for your problem........the only thing I can suggest is to try using
```
ide=nodma
```

When you boot from the CD, at the prompt instead of just pressing enter, type the above and then press enter and see if you have any luck. It worked for me when I installed FC3 a few months ago.

---

### Post by rverwey on 2005-11-15
Thanks for your reply. You&#8217;re right, I misspelled the Ubuntu and Kubuntu.. 

I&#8217;ve tried to enter the code, but I cannot boot from the CD without the installation programme to run. Then, I entered it in the shell function the installation menu offers, but unfortunately it did not set off results. 

I&#8217;ve been searching the internet today and cannot find anything related, except for some other posts mentioning the same error. The exact error is:

Copy remaining packages to hard disk
Copy packages failed
Copying packages to the hard disk failed. You may have run out of disk space in the target /var filesystem, or your CD drive may be having problems reading packages from the CD. Cleaning the CD drive or burning the CD at a lower speed may help.

Check /var/log/syslog or see virtual console 4 for the details.

I indeed burnt another CD at the lowest speed possible (4x150kb). I&#8217;m quite sure that the CD drive is clean. Both CDs stopped at 34% of copying the remaining packages. I have no idea how to access the log file or the virtual console.

Computer details are: HP Pavilion laptop ze5415ea, P4 &#8211; 2.4Ghz, 512 MB internal memory, 40 GB hard disk.

I&#8217;ve read many enthusiastic people about Linux and its interface, so I really want to give it a try, though get discouraged by this error that nobody seems to have..

Again, thanks in advance.

Roy

---

### Post by doconnor on 2005-11-15
Try making another partition called /var.  Make it a couple of gig.

---

### Post by TheWraith on 2005-11-16
[QUOTE=doconnor]Try making another partition called /var.  Make it a couple of gig.[/QUOTE]

I have the same problem, my laptop is an HP dv1000 series and it its about 2 months old and it is my baby (no problems with cd-drive being dirty), i burned the cd at 4x on a 52x burner, both the drive and cd are flawless, yet i still get the error "Copying packages failed" saying i have run out of space in the target /var filesystem. I had originally setup one 17gb "/" dir and one 1gb "swap", got the error. Then, after reading this, i tried creating a seperate "/var" dir. That also resulted in the same error.

---

### Post by rverwey on 2005-11-17
I've been trying again since. I even partitioned the hard drivve 50%/50%, so didnt work.. what can I do more?

---

### Post by doconnor on 2005-11-18
[QUOTE=TheWraith]I have the same problem, my laptop is an HP dv1000 series and it its about 2 months old and it is my baby (no problems with cd-drive being dirty), i burned the cd at 4x on a 52x burner, both the drive and cd are flawless, yet i still get the error "Copying packages failed" saying i have run out of space in the target /var filesystem. I had originally setup one 17gb "/" dir and one 1gb "swap", got the error. Then, after reading this, i tried creating a seperate "/var" dir. That also resulted in the same error.[/QUOTE]

I am new at Linux. 
When I installed I entered expert on the boot line and did a manual setup of the partitions.  I tried to install 3 or 4 times. I tried to install without installing the additional software. That did not work either.
When I had the problem I created a /var partition.  When you say you created a "/var" dir did you mean a "/var" partition?  Did you select the area for the partition and go to another screen where it ask you for the type and mount point(it has names to select for the different possible partitions - /home /usr /var, etc)?  I don't remember whether I clicked or double clicked to get to the other screen. I went to the other screen for each of the linux partitions and selected the type and mount points. I think I only selected the type for the swap partition.  I don't remember whether you selected format on the second screen or the first.  You may have to go thru this second screen so that the installer knows about the /var partition.
After I created the /var partition it worked.  It could have been a coincidence.

---

