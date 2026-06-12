---
title: "A couple of simple questions"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by natebenn on 2008-09-24
Alright guys newb here so bear with me. I've decided after playing with and loving Ubuntu for the last 3 days that I want to reformat my XP/Ubuntu system and start from scratch so I can get the partitions set up right and things. Now I've been reading over at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and found the information really helpful but have just a couple more questions before I go ahead and wipe out this drive.

1. I'm assuming it's best to just write "0"s to this drive and start from scratch right?
2. If I want to dual boot XP & Ubuntu which one should I install first?
3. I get how the partitions should be setup but should I use the live cd to actually setup those partitions or what? 

I'm sure I have more questions but for now that'll do. Any help you guys can give is really appreciated. Thanks ahead of time.

---

### Post by Idefix82 on 2008-09-24
1. Not sure what you mean. When you install a new operating system, you have the option of formatting the entire hard drive before installing.
2. XP first. If you install Ubuntu first then XP will kick GRUB out and you will have to restore it, otherwise you won't be able to see your Ubuntu partition.
3. Exactly. When you install Ubuntu, it will offer you to partition the disk in any way you like. It might be easier though, if you created the partition for Windows first so you don't have to resize it later. All the partitions for Ubuntu are set up during installation of Ubuntu.

---

### Post by lisati on 2008-09-24
1) if you're starting from scratch and re-installing XP and Ubuntu, it shouldn't matter too much about what you write (if anything)
2) It's usually better to install Windows first, as the Ubuntu installer copes better with other operating systems being on the hard drive
3) It's up to you - some people prefer to use gparted (or similar) to set up the partitions first, before installing anything; others are content to let the Ubuntu installer guide them through the process.

---

### Post by natebenn on 2008-09-24
That's what I needed guys, thanks a ton! I should be starting this switch soon so I'm sure you'll see me on here with boatloads of questions. :) Thanks again for the very quick responses.

---

### Post by Sealbhach on 2008-09-24
Yeah, install windows first.

Then in windows create the partition where your Ubuntu install is going to sit.

**_NB:  This is just one suggestion, there are lots of ways to do this, such as separate /boot and /var partitions etc._**

Then, in Ubuntu, I suggest this as a partition scheme:

root folder (mount point = / ) about 10-12 GB

Home folder (mount point = /home) most of the remaining space

Swap folder (mount point = swap) around 2GB

This will make upgrading easier.



.

---

### Post by Idefix82 on 2008-09-24
> **Sealbhach said:**
> Yeah, install windows first.

Then in windows create the partition where your Ubuntu install is going to sit.

Then, in Ubuntu, I suggest this as a partition scheme:

root folder (mount point = / ) about 10-12 GB

Home folder (mount point = /home) most of the remaining space

Swap folder (mount point = swap) around 2GB

This will make upgrading easier.
.
Well, these recommendations are certainly not universal and natebenn will probably be in a good position to decide what he needs after having read the relevant tutorials. For example I would also recommend having a separate boot partition. With lots of RAM I would leave more space for SWAP for smooth suspend/resume. Depending on the applications that will run, a separate tmp partition can also make a lot of sense (for example I regularly use a mathematics package which easily uses half a gig of temporary data per session. I wouldn't want the main partition to get horribly fragmented because of this). The list of possible modifications is rather long. Of course, the general recommendations will work but natebenn did sound like he wanted to get a setup that suits his needs.

---

### Post by Sealbhach on 2008-09-24
> **Idefix82 said:**
> Well, these recommendations are certainly not universal and natebenn will probably be in a good position to decide what he needs after having read the relevant tutorials.

Absolutely, this is just a suggestion. There are probably lots of better schemes.

.

---

### Post by natebenn on 2008-09-24
Again guys thanks for the info on how to setup the correct partition. Let me tell you what I plan to do within Ubuntu and maybe that will help determine my best partition layout. 

Basically I am looking to have Ubuntu replace XP for all I do with the exceptions of games that don't work in Ubuntu. My most basic functions include the web, email, picture management, Itunes (will be replaced with Rhythmbox), ripping movies and playing games like TF2, HL2. I would like to have the ability to upgrade with ease but honestly unless there are major advantages to upgrading I'll probably just stick with 8.04 when I get it working like I need.

So what kind of partition setup would serve my purposes best?

---

### Post by Idefix82 on 2008-09-24
One more piece of info you need to tell us is how much space do you have for Ubuntu and how much RAM do you have/are you going to have in the foreseeable future.?

---

### Post by natebenn on 2008-09-24
I have 2 drives right now an 80gb and a 160gb. The 160 is going to be NTFS storage likely for all my docs, pics and the 80 is what I'll dedicate to the dual boot. I have 2gb of ram as well with no current plans to add any.

---

### Post by Idefix82 on 2008-09-24
Well, I don't think you need a separate /tmp partition. However you might want to have a separate /var partition, it's really up to you. Synaptic uses /var to store the downloaded packages in. You can tell it to delete all this temporary data when you are done installing, but if that resides on your main partition then it will get fragmented rather quickly. At most 1 gig for /var will be enough, but as I said it's not a must.

Your SWAP partition should be at least the size of your RAM if you want to be able to suspend and resume. At suspend the RAM is written into the SWAP space. People usually recommend to have up to twice the RAM as SWAP, but since you don't have that much space, 3 gig will probably do.

Your /home partition probably doesn't need to be that large, since you are planning to store the films and stuff on the other hard drive. But that's up to you to decide. Make it at least 10 gig though.

Finally, to have a more stable system, you might want to have a separate /boot partition. 200 MB is waaay more than enough for that.

The rest can then be occupied by your root partition. That will include all the programs that you install and the operating system itself.

I hope all this makes sense.

---

### Post by natebenn on 2008-09-24
Well I am gonna have to read through that response a couple times more to make sure I get it. I'm not used to all of these partitions; coming from Windows it's just as easy to use the drive in whole, not part it out so it's kind of a new way of thinking. 

If someone has the time and knowledge could you please explain to me the purpose that the /home, /boot or any other common partitions? I'm the kind of person who likes to atleast try and understand things first, I think that'd be really helpful. 

Thanks a ton for the input though Idefix, that will be valuable info when I get around to reinstalling.

---

### Post by Idefix82 on 2008-09-25
The idea is this: a separate boot partition reduces the risk of completely screwing up things. If you do damage to a partition by installing a program badly or if you upgrade something and nothing works any more then at least your boot partition will be ok, so you can replace the upgrade with the older version and just continue working rather than having to reinstall everything.
Also, different folders contain items of different life spans. Eg items in the /var folder get replaced very quickly and so the folder can get fragmented very quickly. Items in the /usr folder (normally your programs) on the other hand rarely change. /home is somewhere in between. There is no point in fragmenting the whole system and having to defragment it frequently if you can confine the fragmentation to one folder. This you do by giving it its own partition.

You did have the same problem under Windows. The only difference is that Windows doesn't have a solution (other than defragmenting the hard drive regularly or putting up with the fact that the system slows down horribly over time).
 
Ask away if anything else is unclear! Understanding things before doing them really is a good idea and I was exactly like you about two months ago.

---

### Post by wongMak on 2008-09-25
Hi,

I would like to try Ubuntu on a comp where WinXP64 is already installed. Do I need create partition before installation, or I'll have option to resize my existing partition and create new one during installation process?

---

### Post by Idefix82 on 2008-09-25
You will have the option of resizing during the installation. But if I remember correctly, this will limit your freedom of creating different partitions for Ubuntu (see my previous two posts). I think if you ask the installer to resize the windows partition it will give you the most generic installation. If you are OK with that, fine. Otherwise you should resize the partition before installing Ubuntu.
Be sure to install the 64bit version!

---

### Post by wongMak on 2008-09-25
Great! I hope it will be enough for testing purposes, then I'll see. Thanks

---

### Post by natebenn on 2008-09-25
Wow, that  explanation  is exactly what I was looking for. I'd rather understand what I'm doing as opposed to just ignorantly following steps 1-10 or whatever. Thanks again Idefix, you have been immensely helpful and I'm sure you'll hear  from me some more with questions. :)

---

### Post by Idefix82 on 2008-09-25
You are welcome!

---

