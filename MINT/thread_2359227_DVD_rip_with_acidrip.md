---
title: "DVD rip with acidrip"
date: 2017-04-21
forum: MINT
---

### Post by paschales on 2017-04-21
Am trying to use **acidrip** to rip a DVD. Have used [this]("http://www.communitytechnology.org.uk/pub/howtoacidrip/howto.html") for reference.
My only prob is I have failed to find a way to rip all the DVD chapters. Can rip a single chapter OK, but alas not all of them in a single output file.

Acidrip's default DVD device is /dev/dvd which is not present on ubuntu. Have tried /dev/sr0, but it didn't work.
As known, ubuntu mounts dvds under the /media directory. Suppose current user is *user365*, and current DVD label is *MYMOVIE*.
DVD is then mounted on the path /media/user365/MYMOVIE.

The only way I can rip a chapter is to add path */media/user365/MYMOVIE/VIDEO_TS/*.VOB* at the Path editbox under the Video source and press the load button. I can then select the first or any other chapter on the listbox underneath and have it ripped one chapter at a time. Have failed to find a way to rip multiple chapters on a single .avi output file though.

Have ensured to check and save the 'Cache DVD', 'Autoload media' and 'Pre-cache video' check-boxes on the Settings tab.

What am I doing wrong fellas?

---

### Post by mc4man on 2017-04-22
you should mention what release of Ubuntu you are using.

---

### Post by paschales on 2017-04-22
Thanks for your reply, for the rec I use mint 17.2 xfce. Apparently  acidrip fails to parse the contents tree and find the longest title, which  typically is the entity containing all the useful chapters. 

I may be wrong, in that I believe my problem has been because the DVD I have been trying to rip is unprotected. Chances are acidrip will be successful with commercial protected DVDs.

The solution to my problem has been to cat every *.vob file containing a useful chapter to my local hdd drive, something like:
** cat VTS_01_1.VOB VTS_01_2.VOB VTS_01_3.VOB > /mnt/depot/vlab/MyLargeVOB.VOB**

Can  then use acidrip to rip from the Path '/mnt/depot/vlab' instead of the  physical DVD device. By pressing the *Load* button, acidrip will locate  MyLargeVOB.VOB which can be ripped under the default values. Personally I prefer the x264 codec which results in a bigger yet of better quality output file.

*Video  preview* can be used as a means to verify that MyLargeVOB.VOB is  rippable, while *detect* should be used to establish the original dimensions  of the product .avi file. On that, usually acidrip seems to be doing a good job.

Have failed to get myself an .mpg output, most probably because I am missing some library. Still .avi works well for me.

Acidrip hides most of the ripping complexities, making it a user friendly, yet a powerful program for the purpose. Would recommend it. 
:popcorn:

---

### Post by Perfect Storm on 2017-04-22
Moved to mint forum.

---

### Post by mc4man on 2017-04-22
Has nothing to do with type of dvd, lsdvd in 14.04 is 'broken' when used by acidrip.
See screen 1, says dvd read ok but nothing shown.
After upgrading lsdvd to the xenial lsdvd package see screen 2, shows the tracks, ect.

You can download & install lsdvd from xenial without any apparent issue, packages here, install with dpkg, for example, 
sudo dpkg -i  /home/doug/Downloads/lsdvd_0.17-1_amd64.deb

[http://packages.ubuntu.com/xenial/lsdvd](http://packages.ubuntu.com/xenial/lsdvd)

/dev/dvd is missing in 14.04, one can use /dev/sr0 or /dev/cdrom
If desired a permanent symlink can be created, but as mentioned not needed here.
```
echo 'KERNEL=="sr0" SYMLINK="dvd"' | sudo tee -a /etc/udev/rules.d/10-local.rules
```

edit; you could also use handbrake, probably superior in many regards
[https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases)

---

### Post by paschales on 2017-04-26
Many thanks for your help, indeed the newer version of lsdvd has solved this issue and now acidrip can parse the contents tree and find the longest title, which is strongly welcomed. 

Also acidrip can grab the title name from the dvd.

---

### Post by bobnn on 2018-02-19
> **mc4man said:**
> Has nothing to do with type of dvd, lsdvd in 14.04 is 'broken' when used by acidrip.
See screen 1, says dvd read ok but nothing shown.
After upgrading lsdvd to the xenial lsdvd package see screen 2, shows the tracks, ect.

You can download & install lsdvd from xenial without any apparent issue, packages here, install with dpkg, for example, 
sudo dpkg -i  /home/doug/Downloads/lsdvd_0.17-1_amd64.deb

[http://packages.ubuntu.com/xenial/lsdvd](http://packages.ubuntu.com/xenial/lsdvd)

edit; you could also use handbrake, probably superior in many regards
[https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases)

Handbrake doesn't seem to be able to preview scenes, to let me figure out if they are the ones I want.  Acidrip does.

Thank you very much!

---

