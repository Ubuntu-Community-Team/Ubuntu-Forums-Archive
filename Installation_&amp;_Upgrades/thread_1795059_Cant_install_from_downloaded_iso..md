---
title: "Cant install from downloaded iso."
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by ExTruckie on 2011-07-02
I have downloaded both 10.04 and 11.04 and burnt them to dvds using Imgburn. 
10.04 fails during verification and will not complete. 11.04 will burn to a disk but when I try to install it I get an corrupt or missing kernel error. 
Is there another place I can get the iso other than from the official website?

---

### Post by tommcd on 2011-07-02
Be sure to check the md5sum of the downloaded iso to be sure it is valid: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Then try using Iso Recorder or Infra Recorder to burn the CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD at the *slowest possible speed* to guard against corrupting the CD.
Then when you boot the CD run the option to check the CD for defects to be sure it is valid: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by sidzen on 2011-07-02
[http://news.softpedia.com/news/Ubuntu-10-04-2-LTS-Is-Available-for-Download-184993.shtml](http://news.softpedia.com/news/Ubuntu-10-04-2-LTS-Is-Available-for-Download-184993.shtml)

Recommend burn at no more than 8X, checking MD5sum after download and before burn

---

### Post by ExTruckie on 2011-07-02
> **tommcd said:**
> Be sure to check the md5sum of the downloaded iso to be sure it is valid: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Then try using Iso Recorder or Infra Recorder to burn the CD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD at the *slowest possible speed* to guard against corrupting the CD.
Then when you boot the CD run the option to check the CD for defects to be sure it is valid: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
Thanks to both of you

I have never had this problem with Imgburn before and I did alot of custom os install disks with it before I switched to Win7 (yes I know!!) I will try the suggested items.
Imgburn does an integrity of the  disk and that is where the 10.04 disk was failing. I'll report back too.

---

### Post by ExTruckie on 2011-07-02
Update

I finally got a good iso for 10.04.2LTS and have it installed and functioning. 

Thanks to all who contributed to the solution.

---

### Post by mörgæs on 2011-07-03
Good, please mark the thread 'solved'.

---

### Post by tommcd on 2011-07-03
> **ExTruckie said:**
> 
I finally got a good iso for 10.04.2LTS and have it installed and functioning. 

Glad you got Ubuntu installed!
So, just out of curiosity, and to help others who may have this problem, what did you do differently this time? 
Did you download the iso image from a different mirror?
Did you use Iso Recorder or Infra Recorder?
Did you simply just burn the iso image to CD at the slowest possible speed?
Did you run the option to check the CD for defects? 

Please provide the details if you can. I am interested to see what exactly worked for you.

---

### Post by ExTruckie on 2011-07-04
> **tommcd said:**
> Glad you got Ubuntu installed!
So, just out of curiosity, and to help others who may have this problem, what did you do differently this time? 
Did you download the iso image from a different mirror?
Did you use Iso Recorder or Infra Recorder?
Did you simply just burn the iso image to CD at the slowest possible speed?
Did you run the option to check the CD for defects? 

Please provide the details if you can. I am interested to see what exactly worked for you.


I was going to when I first posted the update, but I didn't want to write a book ;)

However since you requested,

Since I was having trouble burning the dvd on my windows box using a dual layer burner.
I used my ubuntu box (the one with the trouble) and downloaded the iso onto that machine and used the burner in that machine to burn the dvd. I got the iso from the ubuntu website. 
I used the burning program included in ubuntu to do it. I did make sure that the burn speed was 4x. 
I did not check the dvd for defects.
Thats about all I did to get it installed. I did have a minor glitch with the install so I just reinstalled again an all ok and in less time than updating. 
I must say, I do like the way to select the hard drives to install to on this version.  A lot easier to decipher  
that the old way of sda, sdb

I do hope this is sufficient to help others.

---

### Post by dFlyer on 2011-07-04
> **ExTruckie said:**
> I have downloaded both 10.04 and 11.04 and burnt them to dvds using Imgburn. 
10.04 fails during verification and will not complete. 11.04 will burn to a disk but when I try to install it I get an corrupt or missing kernel error. 
Is there another place I can get the iso other than from the official website?

Be sure to check the md5sum of the iso. You can get the checksum md5sum file from the web page you downloaded your ubuntu iso. If that check out okay than burn the disk to cd/dvd at the slowest speed your burner will allow. Once the disk is burned boot off the cd and when the little stick man appears press the space bar or any key and select check disk. If all the above is okay, they boot to live desktop and test all your hardware including wifi if you have it. If everything checks out go ahead and install from the desktop. If you have any problem post back with error messages and hardware specs.

---

