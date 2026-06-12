---
title: "Unable to find a medium containing a live file system"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by arsh25 on 2011-10-08
While installing Ubuntu,I am getting the error **"Unable to find a medium containing a live file system "**,I am booting from a live CD.Please help.

---

### Post by Rubi1200 on 2011-10-08
Hi and welcome to the forums :)

Please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by arsh25 on 2011-10-08
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.
I am not using an Ubuntu machine at present, i am getting this error during installation just after the loading ubuntu screen.

---

### Post by Rubi1200 on 2011-10-08
Okay, let's start with some basics.

what are the computer specifications, especially RAM and graphics card?

did you check the integrity of the image?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by raja.genupula on 2011-10-08
[http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing](http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing)



look at last five or six posts

---

### Post by arsh25 on 2011-10-08
> **Rubi1200 said:**
> Okay, let's start with some basics.

what are the computer specifications, especially RAM and graphics card?

did you check the integrity of the image?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

256 MB graphics and 1.2 GB RAM. The fle is present in the CD i burnt.How do i do the check?

---

### Post by Rubi1200 on 2011-10-08
What graphics card do you have? Intel, NVIDIA, or something else?

The check can be done on the CD:
When you start the CD you will see an option to check the CD for defects; try this first and let us know what happens.

---

### Post by raja.genupula on 2011-10-08
after inserting the cd , you are going to get the options in that i think there will be a option to test the cd for errors . try that.


all the best.

---

### Post by arsh25 on 2011-10-08
> **Rubi1200 said:**
> What graphics card do you have? Intel, NVIDIA, or something else?

The check can be done on the CD:
When you start the CD you will see an option to check the CD for defects; try this first and let us know what happens.

All i see is 3 options..
1 Live demo and installation
2 Install Inside Windows
3 More Info

I have NIVDIA

---

### Post by raja.genupula on 2011-10-08
Hi 
I think these are the options when you are running WUBI. Dont go for WUBI.choose 1st boot priority as CD/DVD ROM in your BIOS settings and then boot from Ubuntu CD.there you can get ubuntu menu.In that menu look for check disk for errors .Thats gonna do the remaining job.

               All the best.

---

### Post by arsh25 on 2011-10-08
> **raja.genupula said:**
> Hi 
I think these are the options when you are running WUBI. Dont go for WUBI.choose 1st boot priority as CD/DVD ROM in your BIOS settings and then boot from Ubuntu CD.there you can get ubuntu menu.In that menu look for check disk for errors .Thats gonna do the remaining job.

               All the best.

Raja,i dont get that menu when i boot from CD after lading page this error is coming?Is it Machine related or CD related?

---

### Post by raja.genupula on 2011-10-08
seems its cd , could you please give a try with different CD ?

---

### Post by arsh25 on 2011-10-08
> **raja.genupula said:**
> seems its cd , could you please give a try with different CD ?

Should i redownload the torrent file also or just reburn the CD?What's the best way burn the CD?
Also Please help with the MD5 Check.

---

### Post by raja.genupula on 2011-10-08
if you have your iso then check its md5checksum by using this.if it shows any errors then re download the iso.

This link have step-by-step process.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 All the best

---

### Post by arsh25 on 2011-10-08
> **raja.genupula said:**
> if you have your iso then check its md5checksum by using this.if it shows any errors then re download the iso.

This link have step-by-step process.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 All the best

By command line,they mean CMD in windows?Please could you explain in non technical terms?

---

### Post by raja.genupula on 2011-10-08
> **arsh25 said:**
> By command line,they mean CMD in windows?Please could you explain in non technical terms?

Hi 
Sorry for late.
ok you can go with this

[http://linux.koolsolutions.com/2009/02/19/howto-verifying-md5-checksum-on-windows/](http://linux.koolsolutions.com/2009/02/19/howto-verifying-md5-checksum-on-windows/)

---

