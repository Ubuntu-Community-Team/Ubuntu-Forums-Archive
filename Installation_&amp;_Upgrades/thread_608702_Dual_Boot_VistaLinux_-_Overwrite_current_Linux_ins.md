---
title: "Dual Boot Vista/Linux - Overwrite current Linux installation!l"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by sdjcwcba on 2007-11-10
Hi,

I have read through the dual boot installation guides however I just want to be 100% about the safest/best way to install Ubuntu in this case.

The laptop (Advent 8112) came with Vista installed as well as a System Drive (recovery?) of a gig or two on a 120gb Hitachi HD. 

I already have OpenSuse installed however I would like to try Ubuntu - without having to take more space from my Vista partition. 

First time round I shrunk the Vista partition using Disk Manangement in Vista itself...

The maunal installation on the Ubuntu LiveCd shows the following:
```

/dev/sda
/dev/sda1         ntfs       /media/sda1        5767mb(size)4099mb(used)
/dev/sda2         ntfs       /media/sda2        1572mb        524mb 
/dev/sda3         ntfs       /media/sda3        79667mb      35300mb (Vista -- was preivously 120gb)
/dev/sda6         ext3      /media/sda6        12642mb       2400mb
/dev/sda7         ext3      /media/sda7         18967mb      1200mb
/dev/sda5         swap                         1406mb        0mb

```
I am a little unsure on which partitions to format so I can install Ubuntu where openSuse is currently.

Thanks a lot! For now I will continue to read some more of the unofficial guides however I am worried I will mess up
:)

---

### Post by kingof1981 on 2007-11-10
buy more drive's...

[SIZE="1"]the safest way to get dual or three-way boot...
is to disable disk to spin up (load boot-loader)...
the geek way => do it like it is writen on many other sites...
the easy way => do it i bios...
the stupid way => disconnect the power-cable of the selected drive...

run the install Vista or what so ever...
then do it over again for an another OS...

and so reinstall the grub-loader in linux... the grub-loader recognize the winder-boot-loader... so that's it...[/SIZE]

---

### Post by sdjcwcba on 2007-11-10
Heh thanks, anyway to do it without spending more money? (As well as this being a laptop :) )

Joe

---

### Post by rsambuca on 2007-11-10
You can just select "manual partitioning" when installing ubuntu.   You then just need to direct the Ubuntu installer to use /dev/sda6 (or /dev/sda7).  You can use the existing swap partition as well.

---

### Post by sdjcwcba on 2007-11-10
Thanks, when you mean direct the Ubuntu installer to sda6 or 7 do I do that by checking format on either?

---

### Post by rsambuca on 2007-11-10
First, I think you had better make sure you know what is on each of those partitions.  Did you have one data partition or something?

Once you know which one of those you want to install Ubuntu onto, then you would tell the installer to use it for the root '/' directory and format it.

---

### Post by Gremlinzzz on 2007-11-10
go to Vista partition using Disk Management  delete the Linux partitions reformat the partition then delete the partition which makes it free space. then when installing Ubuntu choose== guide use largest continuous free space. that would be goodbye SUSE hello Ubuntu.

---

### Post by rsambuca on 2007-11-10
> **Gremlinzzz said:**
> go to Vista partition using Disk Management  delete the Linux partitions reformat the partition then delete the partition which makes it free space. then when installing Ubuntu choose== guide use largest continuous free space. that would be goodbye SUSE hello Ubuntu.

That is unnecessary to got through all of those steps!  There is no need to use the Vista Disk Manager first.

---

### Post by Gremlinzzz on 2007-11-10
> **rsambuca said:**
> That is unnecessary to got through all of those steps!  There is no need to use the Vista Disk Manager first.

There not that many steps and i do it all the time.removed feisty and installed gutsy that away.you dont have to format you can just delete the linux partitions using  Vista Disk Manager which makes it free space i just format to be sure its a clean partition before i delete it

---

### Post by rsambuca on 2007-11-10
If you are installing over top, the Ubuntu installer will automatically format the root partition, so it is just a complete waste of time.  It obviously doesn't hurt anything, but why?

---

### Post by Gremlinzzz on 2007-11-10
He wants the safest way to do it and he installed SUSE basically that away .its like reverse engineering . what i would be worry about is laptop and Ubuntu most complaints are from laptop users.

---

### Post by rsambuca on 2007-11-10
> **Gremlinzzz said:**
> He wants the safest way to do it and he installed SUSE basically that away .its like reverse engineering . what i would be worry about is laptop and Ubuntu most complaints are from laptop users.

But it isn't the "safest way"!  It is unnecessary and a waste of time.  Of course the OP is free to do it however he/she wishes, though.

---

### Post by Gremlinzzz on 2007-11-10
> **rsambuca said:**
> But it isn't the "safest way"!  It is unnecessary and a waste of time.  Of course the OP is free to do it however he/she wishes, though.

are you dual booting vista and Ubuntu? who knows what leftovers SUSE can leave my way is better.cause i do dual boot vista and Ubuntu.

---

### Post by rsambuca on 2007-11-10
First of all, if you just let the Ubuntu installer format the drive like it always does, then Suse won't leave anything behind, because the partition will be formatted.

Second of all, not that it should make a difference, but no, I do not dual boot.  In fact, I have 7 Operating systems on my PC.  XP, Vista, Ubuntu 64bit, Gentoo, Debian, Sabayon, and Dreamlinux.

Unlike yourself, I think it is important that we give the simplest instructions to people requesting help in the forums.  Telling them round-about methods that require extra steps to do something is just complicating and confusing.

---

### Post by Gremlinzzz on 2007-11-10
> **rsambuca said:**
> First of all, if you just let the Ubuntu installer format the drive like it always does, then Suse won't leave anything behind, because the partition will be formatted.

Second of all, not that it should make a difference, but no, I do not dual boot.  In fact, I have 7 Operating systems on my PC.  XP, Vista, Ubuntu 64bit, Gentoo, Debian, Sabayon, and Dreamlinux.

Unlike yourself, I think it is important that we give the simplest instructions to people requesting help in the forums.  Telling them round-about methods that require extra steps to do something is just complicating and confusing.

but it does make a difference cause i have what the user wants and thats a dual boot of vista and Ubuntu not to install all of distrowatch. if you used Disk Management in Vista then you would see theres nothing confusing about what i suggested and its the safest way to remove a old system and install a new one.

---

### Post by rsambuca on 2007-11-10
> **Gremlinzzz said:**
> but it does make a difference cause i have what the user wants and thats a dual boot of vista and Ubuntu not to install all of distrowatch. if you used Disk Management in Vista then you would see theres nothing confusing about what i suggested and its the safest way to remove a old system and install a new one.

Wrong, but to each his own.  

Let's see:  Your method is to 

1.  Reformat the partition.
2.  Delete the partition
3.  Re-create the partition during installation.
4.  Format the new partition for use.

My method:

1.  Start at your number 4.  Which is easier????

---

### Post by sdjcwcba on 2007-11-10
Thanks for the help - its all working great now (just need to get desktop effects now!). One of the main reason I want to switch to Ubuntu is the very helpful community and forums.

Although one method may be longer/shorter/easier/harder than the other - you both gave me a viable solution to my problem - so thankyou! :)

Joe

---

### Post by Gremlinzzz on 2007-11-10
> **rsambuca said:**
> Wrong, but to each his own.  

Let's see:  Your method is to 

1.  Reformat the partition.
2.  Delete the partition
3.  Re-create the partition during installation.
4.  Format the new partition for use.

My method:

1.  Start at your number 4.  Which is easier????
OK the easy way use Disk Management in Vista
delete the Linux partitions which makes it free space
put Ubuntu live cd in and click install icon
when asked choose guide use largest continuous free space.Ubuntu does the rest safely.

---

### Post by Gremlinzzz on 2007-11-10
> **Gremlinzzz said:**
> OK the easy way use Disk Management in Vista
delete the Linux partitions which makes it free space
put Ubuntu live cd in and click install icon
when asked choose guide use largest continuous free space.Ubuntu does the rest safely.

i win :lolflag:

---

### Post by rsambuca on 2007-11-10
> **Gremlinzzz said:**
> OK the easy way use Disk Management in Vista
delete the Linux partitions which makes it free space
put Ubuntu live cd in and click install icon
when asked choose guide use largest continuous free space.Ubuntu does the rest safely.

You win?  Hardly.

What part do you not understand?  You do not need the Vista steps.  You can start with the Ubuntu liveCD and simply install into the existing partition.

---

### Post by bthoward on 2007-11-10
Don't worry about it rsambuca...  He just doesn't feel comfortable with the Ubuntu installer.  People who are scared of linux tend to gravitate to windows methods so that they only have to use the linux installer in one way and not have it do anything for them.  Its simpler for people who are afraid of linux because more often than not these types of people feel that windows can do no wrong.  

Honestly you both win as you both have "simpler" routes.  One is just simpler for different people.  Personally I'm more for rsambuca's methods.

---

### Post by Gremlinzzz on 2007-11-10
> **rsambuca said:**
> You win?  Hardly.

What part do you not understand?  You do not need the Vista steps.  You can start with the Ubuntu liveCD and simply install into the existing partition.

my way you know what your removing even if your a noob to Ubuntu. your way noobs have erased there windows partition . you know thats true so do i Hardly win now.

---

### Post by Gremlinzzz on 2007-11-10
> **bthoward said:**
> Don't worry about it rsambuca...  He just doesn't feel comfortable with the Ubuntu installer.  People who are scared of linux tend to gravitate to windows methods so that they only have to use the linux installer in one way and not have it do anything for them.  Its simpler for people who are afraid of linux because more often than not these types of people feel that windows can do no wrong.  

Honestly you both win as you both have "simpler" routes.  One is just simpler for different people.  Personally I'm more for rsambuca's methods.

what you butting in for with your 
Beans: 2:lolflag:

---

### Post by rsambuca on 2007-11-10
> **Gremlinzzz said:**
> my way you know what your removing even if your a noob to Ubuntu. your way noobs have erased there windows partition . you know thats true so do i Hardly win now.

That's why I told the OP specifically which partitions were the linux ones.

---

### Post by sdjcwcba on 2007-11-10
I never said which method I used you know? I never will becuase its not going to do any good. 

I just said thanks to both of you :)

---

### Post by rsambuca on 2007-11-10
> **Gremlinzzz said:**
> what you butting in for with your 
Beans: 2:lolflag:

A person's bean count has absolutely no correlation to knowledge.

Just because you don't know how to properly identify partitions and use the Ubuntu installer, it doesn't mean that everyone is so challenged.

---

### Post by Gremlinzzz on 2007-11-10
> **rsambuca said:**
> That's why I told the OP specifically which partitions were the linux ones.

OK truce i call a draw.
even thought i won:lolflag:

---

### Post by bthoward on 2007-11-10
> **Gremlinzzz said:**
> what you butting in for with your 
Beans: 2:lolflag:

Because someone has 2 beans doesn't mean that they are new to linux.  Remember that and you will go far my son.  Also keep in mind that it is people such as yourself who turn people off to linux.  Extra steps just for the sake of extra steps are pointless.  And fighting about it for so long does nothing but gain you beans.  In this example you can easily see how number of beans has nothing to do with level of intelligence.  The more you post whore the higher your score.  Big deal.

---

### Post by bthoward on 2007-11-10
> **jodoog said:**
> I never said which method I used you know? I never will becuase its not going to do any good. 

I just said thanks to both of you :)

I'd bet you used the windows method as you used it before to resize your windows partition.  Most linux installers will do that for you.. Not that it matters to me at all but just figured I'd let ya know.

Glad to hear you have everything working like ya want.

---

### Post by Gremlinzzz on 2007-11-10
> **bthoward said:**
> Because someone has 2 beans doesn't mean that they are new to linux.  Remember that and you will go far my son.  Also keep in mind that it is people such as yourself who turn people off to linux.  Extra steps just for the sake of extra steps are pointless.  And fighting about it for so long does nothing but gain you beans.  In this example you can easily see how number of beans has nothing to do with level of intelligence.  The more you post whore the higher your score.  Big deal.

 level of intelligence yeah your right up there with dumb and dumber

---

### Post by Gremlinzzz on 2007-11-10
> **bthoward said:**
> Because someone has 2 beans doesn't mean that they are new to linux.  Remember that and you will go far my son.  Also keep in mind that it is people such as yourself who turn people off to linux.  Extra steps just for the sake of extra steps are pointless.  And fighting about it for so long does nothing but gain you beans.  In this example you can easily see how number of beans has nothing to do with level of intelligence.  The more you post whore the higher your score.  Big deal.

The more you post whore the higher your score.
why did you call me a whore .don't you know you can get a infraction from someone with Artificial Intelligence:

---

### Post by Gremlinzzz on 2007-11-10
> **Gremlinzzz said:**
> The more you post whore the higher your score.
why did you call me a whore .don't you know you can get a infraction from someone with Artificial Intelligence:

how come my dumb and dumber comment was delete but the other users  word WHORE still remands. :guitar:.

---

