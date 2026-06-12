---
title: "Problems burning iso image"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by bukormen on 2009-12-07
I have tried twice to burn the ISO image of 9.10, but have failed to make a bootable CD. It only burns the ISO image.

I still have the ISO image, so am I burning the CD wrong or has the ISO image become corrupt?

I first installed 8.4 a year ago and it worked fine. I then installed 8.10 over the net and that worked fine to. When I tried to upgrade to 9.4 over the net, that did not work. I have now deleted the HD and clean installed 8.4.

Until I sort out 9.10 I will use 8.4... (And curse myself for wanting to upgrade when 8.10 was doing fine...)

---

### Post by darkod on 2009-12-07
If the CD is not bootable and when you open it you can see the file blabla.iso inside, then you are doing it wrong. In the burning software you have to find option similar to Burn Image to Disc and use that.
When you open the CD it should show files and folders inside, not just one single file (the ISO).
Another alternative is that your computer is set to boot directly from the hdd in BIOS so it's ignoring the CD even if it's bootable. The order for booting in BIOS has to be CD, HDD, etc.

---

### Post by sdsmall on 2009-12-07
I am having the same problem.  I burn the image but the job does not complete normally.

I know how to burn ISO images to dvd but cannot do so with the image that I downloaded (64 bit).  I will download again and try.

---

### Post by darkod on 2009-12-07
> **sdsmall said:**
> I am having the same problem.  I burn the image but the job does not complete normally.

I know how to burn ISO images to dvd but cannot do so with the image that I downloaded (64 bit).  I will download again and try.

If burning doesn't finish correctly it might be corrupted image during download.

---

### Post by sdsmall on 2009-12-07
Already downloaded again and same result.  I then burned to a cd instead of a dvd and the job completed ok (is the iso image for cd different from dvd - stands to reason).

When I attempted to boot from cd i got "isolinux: Disk error 04, ax=4280, drive=ef.

I am losing interest in Ubuntu.

---

### Post by lisati on 2009-12-07
> **sdsmall said:**
> Already downloaded again and same result.  I then burned to a cd instead of a dvd and the job completed ok (is the iso image for cd different from dvd - stands to reason).

When I attempted to boot from cd i got "isolinux: Disk error 04, ax=4280, drive=ef.

I am losing interest in Ubuntu.

Frustrating, isn't it?

Some tips on burning disks can be found here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by darkod on 2009-12-07
Why would you waste dvd for such a small image that fits on a cd? If you are using dvd-rw disc that can be a problem. Also cd-rw.
It's really bad you can't make it work but if the burn process was not finishing correctly it sounds more like it's a problem with burning it, not with ubuntu.
In windows you can try free software called ImgBurn. It's very good for burning images and files too. Just type the name in google.

---

### Post by presence1960 on 2009-12-07
> **sdsmall said:**
> Already downloaded again and same result.  I then burned to a cd instead of a dvd and the job completed ok (is the iso image for cd different from dvd - stands to reason).

When I attempted to boot from cd i got "isolinux: Disk error 04, ax=4280, drive=ef.

**_I am losing interest in Ubuntu_**.
That is not any reflection on Ubuntu, rather it is a reflection of operator error or hardware/software error. Have you done this:
1. [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded ***_prior_*** to burning it as an image to disk?

2. Did you burn the iso as an image at no more than 4x or 8x speed? This will eliminate errors. making a bootable image is far more demading then burning data or music files. One piece of data with an error will ruin the image. If your burning software isn't capable of doing the job see [here ]("https://help.ubuntu.com/9.10/switching/installing-burning.html")for Infra Recorder.

3. Once the above is done boot the Live CD and choose "check disk for defects" prior to doing anything else.

In closing it is not Ubuntu's fault you can't seem to burn a good image to CD. You haven't even gotten into Ubuntu yet. Up until this point it is all you and your machine.

---

### Post by kelvin spratt on 2009-12-07
> **sdsmall said:**
> Already downloaded again and same result.  I then burned to a cd instead of a dvd and the job completed ok (is the iso image for cd different from dvd - stands to reason).

When I attempted to boot from cd i got "isolinux: Disk error 04, ax=4280, drive=ef.

I am losing interest in Ubuntu.

No I use nothing but rewritable media, always use Verbatim never had a coaster in 4 years of burning Linux to DVD+RW. If you use windows use Power ISO, for burning, in Linux Gnome, right click on image and burn.

---

### Post by presence1960 on 2009-12-07
Could be your optical drive. Try cleaning it. Just because it reads CD/DVDs doesn't mean it can boot one.  

Or better yet make a bootable USB if your machine's BIOS is capable of booting from USB.

---

### Post by bukormen on 2009-12-07
> **presence1960 said:**
> 2. Did you burn the iso as an image at no more than 4x or 8x speed? This will eliminate errors. making a bootable image is far more demading then burning data or music files.

I burnt a R-CD, but the DVD-burner gives me a choose of either 18x or 9x, I choose 9x and that may be the reason why it does not work.
I will try with another CD-burner.

---

### Post by darkod on 2009-12-07
> **bukormen said:**
> I burnt a R-CD, but the DVD-burner gives me a choose of either 18x or 9x, I choose 9x and that may be the reason why it does not work.
I will try with another CD-burner.

Burning software only offering 18x and 9x? That doesn't sound right. Get ImgBurn, it's quite good for windows.

---

### Post by bukormen on 2009-12-07
> **darkod said:**
> Burning software only offering 18x and 9x? That doesn't sound right. Get ImgBurn, it's quite good for windows.

I am using Ubuntus burner. Does Ubuntu come with 2 burners? I will look around and see.

---

### Post by darkod on 2009-12-07
> **bukormen said:**
> I am using Ubuntus burner. Does Ubuntu come with 2 burners? I will look around and see.

Oooops. All this time I thought you don't even have Ubuntu yet and you're on windows. I'm quite new to ubuntu and haven't burnt images yet so someone else should give you better advice for ubuntu.

---

### Post by efflandt on 2009-12-07
After you download the iso file then **md5sum whatever.iso** and see if that agrees with the md5sum for the iso file.  Then after you burn the iso to disk, eject and reinsert the disk (if it does not eject automatically after burning), then with the CD mounted, cd to the CD and you should find a file called md5sum.txt.  Your next step is to **md5sum -c md5sum.txt**, to see if md5sum of the CD files agrees with md5sum.txt.

If that is all successful and still no boot from CD, check boot order in BIOS settings and make sure that cdrom boots before hard drive.  Note that it may take awhile and your screen may blank or appear to go off at times.

If it still fails, you may have a hardware issue.  Can you boot any other CD that you burned recently?

---

### Post by presence1960 on 2009-12-07
> **bukormen said:**
> I am using Ubuntus burner. Does Ubuntu come with 2 burners? I will look around and see.

k3b, brasero are what i use. Or right click the iso and choose write to disk.

Did not know you were on Ubuntu, your original post gave no indication.

---

### Post by bukormen on 2009-12-08
> **presence1960 said:**
> Did not know you were on Ubuntu, your original post gave no indication.

I though I was very clear... I did mentioned I used 8.4 and 8.10 and was upgrading to 9.10. Anyway, I have Brasero, so will burn a new CD at the weekend. 

Thanks for all the help!

---

