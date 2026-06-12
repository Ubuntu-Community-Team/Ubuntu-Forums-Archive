---
title: "Older PC installation woes"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by pielam on 2021-05-06
This a rather lengthy read... Just a warning.  :)  Sorry, I tend to be as detailed as possible. (I like to think that this eliminates worthless replies)

Yesterday (5-5-2021), while reading Email on my W10 PC, using Thunderbird, I received a free book offer titled "*Learn Linux Quickly*". I have Ubuntu 18.04 on my other Linux dedicated PC. It runs well, no problems except random lock-ups in the 0AD game app. These constant lock-ups prompted me to try the Win version of 0AD. To my amazement, 0AD didn't lock-up on the Win PC. So, I reluctantly left my Linux PC (still a noob status) & switched back to the Win PC.  :(

Previously, I'd vowed, to myself, to not using Win anymore for various reasons. So I started using Linux Mint Cinnamon. But, it wouldn't install... So, on another forum, someone suggested I try Ubuntu instead of LM. So, I did & it installed W/O a hitch. I ran Ubuntu for a while & liked it fine. Did I miss Win? Maybe a little, but not enough to switch back to Win. That is until I ran into the constant 0AD Lock-ups which I never was able to fix (weeks & weeks went by, never new updates of 0AD) . For a while, (probably a few months) I would play 0AD daily on the Win PC. I was addicted to it. Now though, 0AD is but a distant memory of a game I loved, but couldn't beat in the more advanced stages & maps. Mostly because of my handicap. (poor vision, Lack of good motor skills). Sad to say,  I'm just not fast enough anymore... Oh well, I'm learning to life with it...

Anyway, back to the W10 PC... I D/L'ed the free book & began reading it. It had 2 links. One for Virtual Box & 1 for Ubuntu 20.04. VB seems to have D/L'ed & installed correctly. Ubuntu 20.04 though is giving me problems. I started VB, followed all the steps in the book, to setup VB. I attempted to run the Ubuntu live DVD, but it seemed to hang.  :( 

This morning, I decided to try booting from the Ubuntu live DVD W/O VB. So I loaded the DVD into my optical drive of the W10 PC. I was elated, the Ubuntu DVD was booting! After what seemed to have taken forever, my PC hung. I was forced to remove the DVD & boot into Win.

I decided to try the DVD in my Linux PC hoping that it would work. Nope, I aborted the file system file check, & that's as far as it would go too. (same place as on the Win PC.

So, here I am... Not sure how to proceed or what to try next... I want to check the ISO's checksum, but how?
Do I need to try another flavor of Ubuntu? I don't want to do that as it might would make a difference in the book's language/examples. ???

If you could,  please help a noob.  :)

My W10 PC's specs:

MB         Gigabyte GA-78LMT-USB3 
CPU        AMD FX-3900 (~3.9Mhz)
RAM        Corsair 8Gb DDR3, 4x2
Northbridge    AMD 780G rev. 00
Southbridge    AMD SB700 rev. 00
Graphics card    Nvidea  GE Force 730 - driver version 460.89
Graphic Interface    PCI-Express (not using MB video, disabled in CMOS)
Graphic resolution    1600x900

---

### Post by dddman on 2021-05-07
I have a similar setup.  Win10 and VB for Ubuntu.  I originally loaded a usb stick with 20.04 using Rufus, a no fuss install that just worked the first time out.

[https://rufus.ie/en_US/](https://rufus.ie/en_US/)

Please give us a link to this install book.

---

### Post by rsteinmetz70112 on 2021-05-07
I have some very similar machine running both Ubuntu and Wind 10. I no problems w/Ubuntu I have more problems with Win 10.

First thing I's suggest is running file system check on your Linux machine.

---

### Post by grahammechanical on 2021-05-07
So, what problem do you want us to help you with? 1) Installing Ubuntu in Virtual Box running on Windows 10? Or, 2) Loading a Ubuntu live session from DVD on a machine whose hardware specification we are not informed about?

This link will show you some boot options for Ubuntu

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Please look at section Ubuntu CD Advanced Welcome Page Options and section Changing the CD's Default Boot options. Examine section F6 Other Options. You may need to select nomodeset. If that gets the live session/installer running and the install is successful you can activate a proprietary video driver from Software & Updates>Additional Drivers tab. You need to be connected to the internet at the time.

Which of the two problems is it the answer to? Do not know. It is a worthless reply I know. but those are the only kind of replies  I have.

Regards

---

### Post by pielam on 2021-05-07
> **dddman said:**
> I have a similar setup.  Win10 and VB for Ubuntu.  I originally loaded a usb stick with 20.04 using Rufus, a no fuss install that just worked the first time out.

I tried booting from a flash drive a while back... Don't remember all the details... I don't think I was successful, though.  :(

> Please give us a link to this install book.

Sure, but it's not an "install" book, rather a Linux beginner's (like me) guide...

I'd be glad to share the PDF, just tell me where, but I'm afraid I can't find the exact Email. It was an Email from either howtogeek.com or reviewgeek.com. I can't remember which. I went to their site, but 2 searches proved totally useless, sorry.

---

### Post by pielam on 2021-05-07
> **grahammechanical said:**
> So, what problem do you want us to help you with? 1) Installing Ubuntu in Virtual Box running on Windows 10? Or, 2) Loading a Ubuntu live session from DVD on a machine whose hardware specification we are not informed about?

#1... I haven't used my dedicated Linux PC in a long time... At first because of my 0AD issues then later because of other reasons. I'm still wanting to use Ubuntu again, but I remain confused at this point. 
It's just easier for me to use what I know about (unfortunately, that's Win) for now. 

>  This link will show you some boot options for Ubuntu

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)[URL="https://help.ubuntu.com/community/BootOptions"]

[/URL]Thanks!

> It is a worthless reply I know. but those are the only kind of replies  I have.

Regards

**Not at all! **The info in the link will take me a couple of reads to digest, but I'm sure the info will help. (fingers crossed)

---

### Post by pielam on 2021-05-11
> **dddman said:**
> 

Please give us a link to this install book.


Better late than never. They resent the link (Email). Hope this works...:

[Limited Time]("https://2htg.com/elk/4630/1650636/78726") 

[ATTACH=CONFIG]288440[/ATTACH]

This  book is a practical guide that lets you develop the skills you need to  become a professional Linux system administrator. Linux is one of the  most sought-after skills in the IT industry, and the most popular  operating system deployed in both public/private clouds. Learn the  necessary skills today to become an efficient Linux system  administrator. [Free Download!]("https://2htg.com/elk/4630/1650636/78726")

---

### Post by QIII on 2021-05-11
@pielam

Please do not embed large images.  Some of our users have slow connections or data limits.  Transferring such large files may actually cost them extra money.

Please use the paper clip icon above the text input box to attach images, which will leave an expandable thumbnail.

Also, don't cut and paste formatting like tables from other websites.  That can cause conflicts with the UF formatting.

---

### Post by TheFu on 2021-05-11
>  I want to check the ISO's checksum, but how?
The location where you got the ISO file should also have a number of different checksum text files  - md5sum, sha1sum, sha256sum.  Get those at the same time.

Inside the checksum file(s) will be a checksum using the specific tool and the filename xxxxx-xxxx---xxxxxx.iso
Run the checksum program against the .ISO file you successfully downloaded.

Say I have these files:
```
ubuntu-mate-20.04-desktop-amd64.iso
ubuntu-mate-20.04-desktop-amd64.SHA256
```

```
$ sha256sum ubuntu-mate-20.04-desktop-amd64.iso
a298764d9d2615c6fc5e99c7dddd9d7687f885821e6915c57daf9747b9c33445  ubuntu-mate-20.04-desktop-amd64.iso

```
manually compare the output you get with the output from the checksum file.  Using **grep** might make that easier.

```
$ grep a298764d9d2615c6fc5e99c7dddd9d7687f885821e6915c57daf9747b9c33445 *56
ubuntu-mate-20.04-desktop-amd64.SHA256:a298764d9d2615c6fc5e99c7dddd9d7687f885821e6915c57daf9747b9c33445
```

"*56" is just a file pattern thing. I'm lazy, that's all.

Sometimes there's just 1 checksum file for all the ISOs, so the grep will show just the lines that match.

sha1sum, md5sum, sha256sum are examples of the checksum programs.

---

### Post by pielam on 2021-05-12
> **QIII said:**
> @pielam

Please do not embed large images.

Sorry, that was completely unintentional. I also didn't realize that the image would turn out to be so large.  It wasn't **THAT **large in its original form. (In my Email message). It inexplicably became large in the UF post after I pasted it.

> Please use the paper clip icon above the text input box to attach images, which will leave an expandable thumbnail.

Thanx for the explanation. I will attempt to do so in the future.

>  Also, don't cut and paste formatting like tables from other websites.  That can cause conflicts with the UF formatting.

OK. As stated above, that was not my intent. I simply highlighted the portion of the message. that I wanted, copied it, then pasted it in my reply. I had no idea that would cause all this disruption or possibly break something. I am completely unaware of Thunderbird's tables & formatting techniques.

---

### Post by pielam on 2021-05-17
I recently tried loading the live DVD onto a third Everex Explora GA-32 (stock except for a HDD upgrade) that was given to me. It too failed to load the Ubuntu 20.04 live DVD. I was able to invoke the options menu. It seemed to help, but this Everex PC hung too. The errors are as follows:

---[ end kernel panic - not syncing: no working init found. Try passing init = option to kernel. See Linux Documentation/admin-guide/init.rst for guidance ]---

Above this error on the screen are more listed errors. 

This same screen occurred with the other 2 PCs. (The 1st 2 options & the F6 (other Options menu items.))

This all seems very grim to me, what does it mean?

---

### Post by TheFu on 2021-05-17
> **pielam said:**
> This all seems very grim to me, what does it mean?

You get what you pay for?
Sometimes somebody else's junk is just junk.

---

