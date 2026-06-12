---
title: "Karmic Buggy as Hell"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by isTHEr3mOr3 on 2009-10-24
For me that is... 

- Encountered Grub error 22 
- Firefox crashes continuously when it smells flash, so no youtube for me. 
- unable to mount without root 

I am not really intimidated by failures like this, but this will absolutely drive a newb nuts. All these errors are ancient ones that always seem to return. 

Too bad, because I really like this release. It is uberfast!

Just remembered I also had a problem with audio. Could solve it pretty fast by adding rights to use audio for the default user.

---

### Post by oboedad55 on 2009-10-24
Those are very strange and serious errors. Is it possible you got a bad burn?

---

### Post by FuturePilot on 2009-10-24
Are you running 64bit with the 64bit Flash plugin?

---

### Post by priegog on 2009-10-24
I second the Firefox and flash problems. It is super unstable. A shame since Jaunty got flash right.
@FuturePilot:
Yeah, I am running 64-bit. I don't know what kind of flash I have, I only installed ubuntu-restricted-extras, and that is what I got. 
Synaptic says the only flash-related package I have is flashplugin-installer (version 10.0.32.18ubuntu1)

---

### Post by Iehova on 2009-10-24
I second oboedad55... personally I'm on 64 bit and Karmic's been incredibly un-buggy: neither Karmic nor Firefox nor flash nor Grub nor anything except Gwibber has crashed on me IIRC. Having said this I installed post-beta, whereas an earlier install continuously updated may, AFAIK, retain some problems.

---

### Post by slakkie on 2009-10-24
> **isTHEr3mOr3 said:**
> For me that is... 

- Encountered Grub error 22 


[https://answers.launchpad.net/ubuntu/+source/grub/+question/749](https://answers.launchpad.net/ubuntu/+source/grub/+question/749)

> 
- Firefox crashes continuously when it smells flash, so no youtube for me.


I had this problem back in the alpha days. You are running 32/64 bit? getconf LONG_BIT
 
> 
- unable to mount without root 


Unable to mount what as non-root-user? External devices, network shares, etc etc.

---

### Post by isTHEr3mOr3 on 2009-10-24
> **slakkie said:**
> [https://answers.launchpad.net/ubuntu/+source/grub/+question/749](https://answers.launchpad.net/ubuntu/+source/grub/+question/749)



I had this problem back in the alpha days. You are running 32/64 bit? getconf LONG_BIT
 


Unable to mount what as non-root-user? External devices, network shares, etc etc.

I am not trying to solve these problems with this thread. I just think it will be very hard for Linux to ever gain a significant marketshare when these problems still pop up after all these years of development. 

Of course there is a solution to the grub 22 problem (I was able to make the first post with Karmic). 
Of course there is a solution to my mount issue of external devices (probably by adjusting fstab). 
And yes I have a 64 bit computer. 

My biggest concern is that Puppy Linux (basically a one mans hobby) has less issues than Ubuntu. It has its issues too, but I am always able to boot it, get internet going and  flash is already nicely integrated in the browser after install. I really want Ubuntu to succeed, but it will never be successful with errors like this. What is that for an error message anyway... error 22?!? The OS should advise you how to solve this. 

 I guess we need to wait for Chrome OS to make Linux usable for Joe average.

---

### Post by 00b00nt00 on 2009-10-24
Too bad for you, but most of us have a good experience with Ubuntu. Don't make generalisations - there's something peculiar to your system.

---

### Post by slakkie on 2009-10-24
> **isTHEr3mOr3 said:**
> 
My biggest concern is that Puppy Linux (basically a one mans hobby) has less issues than Ubuntu. It has its issues too, but I am always able to boot it, get internet going and  flash is already nicely integrated in the browser after install. I really want Ubuntu to succeed, but it will never be successful with errors like this. What is that for an error message anyway... error 22?!? The OS should advise you how to solve this. 


You can't compare Puppy Linux with Ubuntu. I got grub erros when I wanted to boot Puppy Linux. I think it is great flavor, but I would only use it as a liveCD/USB OS. Or maybe as some kind of server OS on really old hardware.

The error is from grub, not Ubuntu. And if you want the OS to solve it, grub should be able to mount the disks and load the OS. If it cannot do that, how should it solve your grub error? Your beef is with grub, not Ubuntu in this case.

---

### Post by rtalcott on 2009-10-24
I gave up Firefox for Chromium and it's faster and much more stable...no flash problems...I'm running the latest 64 bit KK.

I have some Samba issues on machines that were clean installed using a Daily Build shortly before the Beta...other than that KK reminds me of the Unix Workstations I worked on 15 years ago...fast and stable...I am very impressed!
rt

---

### Post by isTHEr3mOr3 on 2009-10-24
> **00b00nt00 said:**
> Too bad for you, but most of us have a good experience with Ubuntu. Don't make generalisations - there's something peculiar to your system.

I am not so sure about that, grub errors are very common. There is even a boot cd (supergrub) created to help people solve this. 


> **slakkie said:**
> You can't compare Puppy Linux with Ubuntu. 

Why not?

> **slakkie said:**
> 
I got grub erros when I wanted to boot Puppy Linux. I think it is great flavor, but I would only use it as a liveCD/USB OS. Or maybe as some kind of server OS on really old hardware. 

Puppy has a great philosopy.. basically KISS. Don't use stuff that makes it harder or give more bloat. That is why they still use Seamonkey. If you concider the size of Puppy it is amazing they always seem to beat the big players when it comes to detecting hardware. 
Indeed the usage of Grub for a frugal install is a bit harder, that is why it is not the default option. Only for the more advanced users. 


> **slakkie said:**
> 
The error is from grub, not Ubuntu. And if you want the OS to solve it, grub should be able to mount the disks and load the OS. If it cannot do that, how should it solve your grub error? Your beef is with grub, not Ubuntu in this case.

I don't agree. Ubuntu is the collection of all the programs it uses. They also make changes to other programs, they could make Grub more user friendly. 

> **rtalcott said:**
> I have some Samba issues on machines that were clean installed using a Daily Build shortly before the Beta...other than that KK reminds me of the Unix Workstations I worked on 15 years ago...fast and stable...I am very impressed!
rt

Speed of browsing with Firefox did impress me as well. It was really much faster than 9.04. In the beginning flash did work for me a couple of times though, so don't jump to conclusions yet.

---

### Post by slakkie on 2009-10-24
> **isTHEr3mOr3 said:**
> 
Why not?


Let me rephrase, I would not compare the two. I could compare Puppy Linux with DSL.

> 
Puppy has a great philosopy.. basically KISS. Don't use stuff that makes it harder or give more bloat. That is why they still use Seamonkey. If you concider the size of Puppy it is amazing they always seem to beat the big players when it comes to detecting hardware. 


I agree Puppy is a great OS, I've played with it myself.

> 
Indeed the usage of Grub for a frugal install is a bit harder, that is why it is not the default option. Only for the more advanced users. 

I don't agree. Ubuntu is the collection of all the programs it uses. They also make changes to other programs, they could make Grub more user friendly. 


So with puppy it is not bad that you get Grub errors, but with Ubuntu it is? And Ubuntu doesn't develop Grub btw.

---

### Post by 23meg on 2009-10-24
[QUOTE=isTHEr3mOr3]I am not trying to solve these problems with this thread.[/QUOTE]

If you're not trying to solve or report problems, your thread is out of the scope of this forum. If you'd only like to reflect on the quality of Karmic and your experience with it, you can do that in the Ubuntu Testimonials and Experiences forum once it's released.

If you need help troubleshooting those problems, do a forum search to see if there are related threads, and if there are none, feel free to start separate, appropriately titled threads and ask for assistance.

---

### Post by UKBB on 2009-10-24
> **priegog said:**
> I second the Firefox and flash problems. It is super unstable. **A shame since Jaunty got flash right.**

LOL! Not from where I'm sitting they didn't.

---

