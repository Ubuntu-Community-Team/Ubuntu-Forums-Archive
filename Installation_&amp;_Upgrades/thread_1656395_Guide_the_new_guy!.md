---
title: "Guide the new guy!"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by b18turboef on 2010-12-30
Alright well hello everyone, I'm the new guy here. I've spent a few hours reading and I'm really liking the idea of trying this all out. I have what I feel is a good grasp on the idea of how this will all work out, but I would like to make sure I'm not doing things wrong, and need some input as the info I'm looking for has been harder to find than a basic install.

So you know I'll be using:

(not sure if other newegg users can click this or not)
[https://secure.newegg.com/WishList/MySavedWishDetail.aspx?ID=12132754](https://secure.newegg.com/WishList/MySavedWishDetail.aspx?ID=12132754)

amd 1055t x6 processor
ga-890fxa-ud5 mobo
r5450-md512h vid card
ocz vertex 2 60gb ssd
samsung f3 1tb drive
4gb ddr3 g.skill

I'm planning to run Win7 Pro, mostly due to using win my whole life. That being said I'd like to transition to ubuntu but will currently always need windows for work specific programs. This will be my first SSD build and from what I can tell with the windows aspect I need to turn on TRIM support to maintain speed over time, no big deal I'm sure I can manage that. Where I'm a bit confused is I don't seem to see that many threads about both win7 64 bit and ubuntu 64 bit being installed on the same SSD. I'd absolutely love it if I can get both OS's on the same drive, including programs etc, and keep all data (pics, docs, music etc) on the 1tb drive. From what I gather sharing of the files seems to be possible, but I'm not confident I fully understand the process. 

Now to me it seems like it should all be possible, but I want to make sure I'm not going to sacrifice anything by doing so. If need be I'll grab a small extra SSD to boot ubuntu, or maybe a flash drive? Who knows. This will all be brand new hardware, and a blank slate. So being that you all clearly have more experience, if you could guide me in the best, most user friendly way to go. I'd sure appreciate it! I'm always around so if I need to post more info I'll respond within minutes. Thanks again everyone!

---

### Post by b18turboef on 2010-12-31
70 views and no ideas??

---

### Post by Frogs Hair on 2010-12-31
I don't think it's possible for others to access your wish list because the account user name and password are private for good reason. You could add links to the individual components .

---

### Post by b18turboef on 2010-12-31
> **Frogs Hair said:**
> I don't think it's possible for others to access your wish list because the account user name and password are private for good reason. You could add links to the individual components .

I only posted it to show the items being used for the build, but then listed the only ones of importance below the link.

---

### Post by b18turboef on 2011-01-01
Anyone?

---

### Post by Jetso on 2011-01-01
I'm sorry, but I don't understand the question. Are you wondering if Ubuntu will run right on the components you picked? Please restate.

---

### Post by irockonguitar on 2011-01-01
I don't know much about whether this or that is better than what, but have you read Herman's site about dual booting? 

[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

That's the guide I used to get mine set up, though I'm currently having problems getting Ubuntu to boot, but I seem to be getting some help from a few people on here. :)

---

### Post by b18turboef on 2011-01-01
I get the impression I should be fine hardware wise, I just posted the hardware so it was known. My question is regarding the use of the SSD. Does that make ANY difference as far as the installation goes? I'm not sure if being on an SSD will cause issues, or how to get windows 7 on ntfs, and ubuntu on ext4 on the same drive. Also will TRIM cause issues?

I'm essentially wondering what I should do, and maybe I should just use separate drives, or maybe I can just boot ubuntu from a 16gb flash drive or something?

---

### Post by Jetso on 2011-01-01
Oh, okay sorry. I'm not sure because I have never used a SSD. I'm not sure if it's possible, but you have a hard drive on the hardware list so why don't you just put Ubuntu on there. If that is the case, I can guide you on how to do that with no problems for the most part.

---

### Post by b18turboef on 2011-01-01
I guess I could do that, but I was hoping to have them both on the SSD for performance. The 1tb drive is (currently) for data as in music, docs, pics etc. But maybe I need to separate the OS's of different drives?

---

### Post by Ahava591 on 2011-01-01
I don't think dual-booting should be a problem on the SSD; you'll make a partition for Windows 7 and a partition for Ubuntu, (or whatever distro you want,) and each will use its' own file system. They should be happy together, as long as you have enough space on the drive for both.

I suggest you search with Google for that particular model of SSD and use with Linux; I haven't heard of any problems yet but it's good to check.

As for TRIM, the Linux kernel has supported it I think fully since early 2010; I don't anticipate any problems with it as long as your SSD works with Linux. That's why I recommended you search for that model and Linux support.

Good luck, and please feel free to ask us anything more, :)

---

### Post by b18turboef on 2011-01-01
Thank you! Its a 60 gig drive so I don't see any issues with space for just the two OS's. Maybe partition it 45 for windows and 15 for ubuntu. That being said all of the 'install guides' I read keep talking about partitioning AFTER windows exists on the drive, and having to shrink the partition. When I initially install windows 7 on the drive, couldn't I just create the partition at that time? I'd rather not fool around changing its size after the fact if I don't have to.

---

### Post by Jetso on 2011-01-01
One problem I see is that it's a 60GB SSD and that might not give you alot of room for linux. Windows takes alot of room, and if you start to really take Ubuntu seriously and use it every day, then Linux can take up some room, which might not be good on a 60 GB drive. Maybe if you got a bigger SSD you would be better off.

---

### Post by Jetso on 2011-01-01
I just read your new post, and thats exactly what I was talking about. 45 on Windows will fill up quickly, and I have 15GB for Linux and I am quite worried that it is not going to be enough because I have 1.5 GB left, and resizing the Linux partition AFTER THE FACT is dangerous.

---

### Post by b18turboef on 2011-01-01
> **Jetso said:**
> One problem I see is that it's a 60GB SSD and that might not give you alot of room for linux. Windows takes alot of room, and if you start to really take Ubuntu seriously and use it every day, then Linux can take up some room, which might not be good on a 60 GB drive. Maybe if you got a bigger SSD you would be better off.

That may be true? But from what I read most people say you just need 10 gigs to be fine on linux, I figure I'll give it 20 just to be safe. Then windows 7 takes 16gb, and it would have roughly 40, so I'd assume that would work too?

Maybe I should throw two SSD's in there? Or would I be better off just running linux off of a normal hdd?

---

### Post by b18turboef on 2011-01-01
Ok I'll def keep that in mind. I thought they would have plenty of room with ~40gigs/20gigs being that ALL of the data will be on the 1tb drive. The only things installed on the SSD are the OS and associated programs, but none of the music, videos, documents, pictures or any of that stuff.

---

### Post by kevxh on 2011-01-01
Hi, First of all welcome to Linux - wise move :)

To install them both is very straight forward. Install Windows first and rather than just letting the Windows setup program partition the whole disk for Windows do a custom and set it up yourself. Regardless of what you choose Windows will override you and create a boot partition and a data partition. Nothing you can do about that.

Once you've enjoyed to lengthy install process and setup your drivers etc boot from your Linux cd or whatever and install them side by side (the default), ten minutes later you'll be running. Linux will access any NTFS partitions straight away.

It really is that simple :) Enjoy

Kev

---

### Post by Ahava591 on 2011-01-01
> **b18turboef said:**
> Thank you! Its a 60 gig drive so I don't see any issues with space for just the two OS's. Maybe partition it 45 for windows and 15 for ubuntu. That being said all of the 'install guides' I read keep talking about partitioning AFTER windows exists on the drive, and having to shrink the partition. When I initially install windows 7 on the drive, couldn't I just create the partition at that time? I'd rather not fool around changing its size after the fact if I don't have to.

That sounds like enough space, remember to include your swap partition, I forget what Windows calls theirs'. As has been noted, however, that's really not a lot of space for actual use. Once you have both operating systems on the SSD, there's not going to be much room for application software and personal files, (games on Windows, office suites, pictures, music, etc.)

-This is where your HDD comes in, and it's good that you thought of that. Just keep in mind that if you want to put anything on the SSD, you're going to be on a space-budget, so to speak.


I haven't done a Windows 7 install in a few months, but I think there's an option at installation to partition the hard drive beyond the default; you might try running the installation disk up to the point where it asks you how you want to partition the drive and check then. 

If that doesn't work, or if it's not an option, it's really painless to create a partition for Ubuntu at the time you install it; is there any particular reason why you don't want to do that?

---

### Post by b18turboef on 2011-01-01
> **Ahava591 said:**
> That sounds like enough space, remember to include your swap partition, I forget what Windows calls theirs'. As has been noted, however, that's really not a lot of space for actual use. Once you have both operating systems on the SSD, there's not going to be much room for application software and personal files, (games on Windows, office suites, pictures, music, etc.)

-This is where your HDD comes in, and it's good that you thought of that. Just keep in mind that if you want to put anything on the SSD, you're going to be on a space-budget, so to speak.


I haven't done a Windows 7 install in a few months, but I think there's an option at installation to partition the hard drive beyond the default; you might try running the installation disk up to the point where it asks you how you want to partition the drive and check then. 

If that doesn't work, or if it's not an option, it's really painless to create a partition for Ubuntu at the time you install it; is there any particular reason why you don't want to do that?

I don't do games at all, and as I said all data will be on the 1tb drive, I think I can make the size be ok for me. If not I'll figure that out later. If your confident I can just do a normal install on the SSD with windows 7 and ubuntu will partition the drive safely at the time of install then thats totally fine. I just figured I'd be "helping" by creating the partition prior to installing.

---

### Post by b18turboef on 2011-01-01
Forgive the ignorance but what do you mean by 'swap' partition?

---

### Post by Ahava591 on 2011-01-01
> **b18turboef said:**
> Forgive the ignorance but what do you mean by 'swap' partition?
It's basically a part of your SSD/HDD that's used as working memory.

---

### Post by b18turboef on 2011-01-01
> **Ahava591 said:**
> It's basically a part of your SSD/HDD that's used as working memory.

I assume if I just do a normal windows7 install it will handle that on its own?

---

### Post by Ahava591 on 2011-01-01
> **b18turboef said:**
> I assume if I just do a normal windows7 install it will handle that on its own?

Yeah, it will create it automatically; they call it something else for Windows, but when you install Linux it will also automatically create it. In Linux this is called a swap partition. 

The swap partition will be created automatically at installation with Ubuntu and most other distributions, you won't have to do the math and figure out how much space to set aside for it or anything; it will calculate that on its' own and do the work.

---

### Post by Jetso on 2011-01-02
Whoops. I completely forgot about that. Swap is a partition that Linux uses (Although, to be honest I have no clue why.) It is supposed to be 2.5 times your RAM, so for you that would be 10GB. Like I said, if you make a mistake with the sizing now, it is a pain in the a$$ later.

---

### Post by b18turboef on 2011-01-02
> **Jetso said:**
> Whoops. I completely forgot about that. Swap is a partition that Linux uses (Although, to be honest I have no clue why.) It is supposed to be 2.5 times your RAM, so for you that would be 10GB. Like I said, if you make a mistake with the sizing now, it is a pain in the a$$ later.

Maybe someone can explain this in more detail? First off I don't know what swap really is used for, nor does it make sense that it would be related to my ram size?

---

### Post by Jetso on 2011-01-02
To be honest, I really don't know. I should actually know more about it, but I don't. You would have to ask someone else in these forums.

---

### Post by Ahava591 on 2011-01-02
> **b18turboef said:**
> Maybe someone can explain this in more detail? First off I don't know what swap really is used for, nor does it make sense that it would be related to my ram size?

 The swap partition, (there's also something in Linux-world called a swap file, which a lot of people say is better to use than an actual partition and which I have no experience with,) is a portion of storage space used as memory, or RAM.  It's a part of your hard drive, or solid-state drive, that is set aside specifically to handle pages of memory.
Every program is loaded into your RAM when it starts; the area, or amount, of RAM that each program takes up when it runs is composed of things called "pages;" these memory pages can be copied onto your hard drive, or SSD, for various reasons.  

One reason the swap partition exists is this: You're running out of main memory, you have such memory intensive programs running or so many programs running that you've used up all your RAM for the moment; this is where you can use part of your hard drive like RAM. The problem is that your hard drive is much, much slower than RAM. Solid-state drives are comparatively closer to being as fast as RAM, when you consider how slow a hard disk drive is.
One advantage of a swap partition, though, is that some programs have parts that are only really used during start-up; so instead of keeping those start-up parts in RAM the entire time you're using the program, you can set them in main memory when you really need the speed and then set them aside into your swap partition.
-You still need those parts of a program to be running, but you don't really need them to be wasting RAM.

I hope this helps you understand why we've recommended the things we have, and please let us know about any other questions. :)

---

### Post by Jay Car on 2011-01-02
> **b18turboef said:**
> Maybe someone can explain this in more detail? First off I don't know what swap really is used for, nor does it make sense that it would be related to my ram size?

In Windows it's called the Page File, or virtual RAM, and here's a [Microsoft explanation]("http://support.microsoft.com/kb/2267427") for what it does and how it works. Deciding the amount needed for the pagefile does, indeed, have to do with the amount of system RAM installed, as well as what you'll be using the system for.  Unless you do gaming or video editing, it's generally not necessary to mess with the page(or swap) file because it's all set up during installation. 

I could be misunderstanding your concerns, but it seems like you are worried that a dual-boot with Ubuntu and Win 7 might be very complex, or that there may be unforeseen problems on your new SSD.  Certainly things can go awry whenever computers are involved, but what you are trying to do is really not that difficult.

My son recently installed Ubuntu 10.10 along-side Win 7 on a new SSD (though I believe it was an 80GB drive) and said that it all went smoothly and works great. "Fast and sweet" were his words.

Here's [a good place to start the process]("https://help.ubuntu.com/community/WindowsDualBoot"). 

Hope this helps.

---

