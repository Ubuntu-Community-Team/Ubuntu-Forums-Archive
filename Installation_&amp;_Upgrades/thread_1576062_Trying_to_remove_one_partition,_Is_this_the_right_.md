---
title: "Trying to remove one partition, Is this the right way?"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by Rasa1111 on 2010-09-16
Hey all, 

  I recently "hosed" my 10.10 install, by (blindly) letting the "partial upgrade" to do its thing. 
After the partial upgrade, and upon reboot,
 10.10 would only boot into shell. 

Rather than doing a whole bunch of stuff in shell that im not comfortable with,
I would rather just delete the partition that I installed 10.10 on, and reinstall it the same way I did to begin with. 
(and this time stay away from "partial upgrade") now that i know better. lol

 
 Here is my question(s)...

 In this screenshot,  I can see that there is the option to "delete" a partition, 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169676&stc=1&d=1284668245[/IMG]


 My 10.04 install is on /dev/sda1 (green) 29.9 GB

 My 10.10 install is apparently /dev/sda6 (orange) 8.1 GB

Can I, simply highlight the /dev/sda6 partiton, and choose "delete" ?

 and that will only delete that partition? 

 In turn, giving all space back to /dev/sda1 , So I can then create a new partition to reinstall 10.10 on it? 


I also see that I have 2 swaps ,  on /dev/sda5, and on /dev/sda7.

 I was recently informed by a forum member, that only one is needed.
(not even sure how I got 2, to be honest)

 But, If I can simply choose to delete the sda6 partition,
could I also do the same thing with one of the swaps? If both are not needed? 

and if so.. which swap would be best to delete? 
the 412 MB, or the 1.7 GB ? 

and, If I do this,  it *should* leave my sda1 partition alone, right?

Hope Im being clear enough,  but if not, please let me know and I will try to be more understandable. 

So basically, my wished for goals are this, 

To get rid of the partition that now has the borked 10.10 install, 
to remove one of the un-needed 'swaps', 
and then create a new partitoon (again), to reinstall 10.10 on. 
all without borking my 10.04 install. 

 Does this sound easy enough? 

 If so, I would greatly appreciate any enlightenment anyone can provide me. 

 Many thanks, 
Looking forward to replies. :)
<3
Rasa

---

### Post by Rasa1111 on 2010-09-16
Here is the rest of the partition 'line', that was cut off in  previous pic.
Not sure if it's needed, but just in case~
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169680&stc=1&d=1284669692[/IMG]

 thanks.

---

### Post by uRock on 2010-09-16
Yes, you can delete sda6, if you install 10.10 and let its grub replace 10.04's then you may have to reinstall grub from a LiveCD.

As far as swap goes, remove the one NOT used by 10.04, you can tell which one is being used by running the free -m command or looking in System Monitor. This will save to pain of telling 10.04 to use the different swap. Chances are that the smaller swap (sda7) was made by the 10.10 installer, but you still want to double check to makes sure.

If 10.04 is handling grub, then you will have to run update-grub to get it synced with what is installed.

Let me know if I missed anything.

---

### Post by Rasa1111 on 2010-09-16
Thanks for the quick reply, uRock. :) <3
you rock! lol  ;)

Ok, free -m gives me this~
>  ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1000        902         98          0        111        507
-/+ buffers/cache:        283        716
Swap:         2002          0       2002


Im not 100% sure at what Im looking at or how to tell which one should be removed. :?:
Probably the smaller one, as you said, But Im not sure. :/ 
Does that readout let *you* understand which one I should remove? 

Hate to admit it, but I am a little confused by this~
 > if you install 10.10 and let its grub replace 10.04's then you may have to reinstall grub from a LiveCD.


Im really not sure how I would even "let" 10.10's grub replace 10.04's. ?
and if i had,  Im not sure how to reinstall it from the liveCD. 

Is there a simple way to tell which version , 10.04, or 10.10 is handling grub? 

Sorry for all the simpleness,  The most Ive done thus far with partitions, is to create them. lol
But this is my first major goof in Ubuntu (borking 10.10), 
So I just want to be as sure as I can. that I dont do anything that I cannot fix later. 

 i mean, I know that if worse came to worst, 
I could simply reinstall 10.04 and use the whole disk,
but i have it near perfect now and It would take awhile to get it back to how it currently is. 

 Thanks so much. :) <3

---

### Post by uRock on 2010-09-16
You'd have to run the free command from within the 10.10 install.
```
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1000        902         98          0        111        507
-/+ buffers/cache:        283        716
Swap:         2002          0       2002 			 		
```Is showing that the LiveCD is using both swaps, because one is 1.6GB and the other is .4GB and it is showing that you are using 2.002GB, which is a little off, mathematically.

As for the grub, when you last installed 10.10, did you tell it to install grub into the sda6 or did you let it do the default? If it did the default then you will either have to let your 10.10 reinstall install grub for the system(default) or use the 10.04 LiveCD and [follow these directions]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") to get 10.04's grub back in control.

---

### Post by Rasa1111 on 2010-09-16
But how would I do that if I cant get into the 10.10 install? 
I mean, I can get into shell, and login,  but nothing else. 
So would i just run the command from shell? 

 When i installed 10.10, I did not specify that it do anything with grub,
so it must be whatever is done by default. 

 crap, knew I shouldnt mess with things im unsure of..
doh. :(

---

### Post by uRock on 2010-09-16
I'd say go ahead and let the new install of 10.10 install its grub. I would think at this point it should be good to go.

Delete the smaller of the two swaps and if we find that the 10.04 install was using it, then we can tell it to use the other one with a few quick commands from this tutorial. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Rasa1111 on 2010-09-16
cool, thanks man. <3

So to be sure before I go clicking,
 I can "delete" the 10.10 partition, and the smaller swap,..  yeah?

which, in turn, would leave me with 10.04 on the whole hdd, right? 

 and then I would simply go through the new 10.10 install as normal, and specify how much space it should get? 

 Thanks again man, I really appreciate it. :D

---

### Post by wilee-nilee on 2010-09-16
uRock gave you all the good stuff, you might find it easier to edit the HD and partitions with gparted, and then set up the partition to install to, from in gparted. Then as you are, use the custom install to put the OS in your pre-formatted partition.

You always turn the swap off in gparted for these operations, and you can only change unmounted partitions. So you could if you wanted adjust other unmounted partitions from a regular running OS, just not the one your running, with gparted.

---

### Post by uRock on 2010-09-16
Does the 10.10 partitioner allow you to install in the largest unused partition? If yes, then use that option. If not, then to use that free space you will have to select partitions manually. The cool part with that is that you get to tell it to use the same swap.

---

### Post by Rasa1111 on 2010-09-16
hey wilee, thanks for dropping in mate. :)

 I'm sorry, now I'm just more confused than I was before. lol :(

> Does the 10.10 partitioner allow you to install in the largest unused  partition? If yes, then use that option. If not, then to use that free  space you will have to select partitions manually. The cool part with  that is that you get to tell it to use the same swap.     

 same thing with this. :( lol

largest unused partition? 

 I dont think there is an "unused" partition. 

 I dunno, 
I guess I should probably just quit, and cut my losses for 25 days or so,
and just boot into my 10.04 while I still have it alive. 

 Pretty upset with myself about now. 
1, for screwing up the install, and 2 for not fully grasping what's being told to me. DOH.

 It would really suck big time if I suddenly couldn't get into that. :(
meh. 

thanks for your time, 
it's greatly appreciated. <3
+karma to you both.

---

### Post by uRock on 2010-09-16
My apologies, unused=empty. It was avail in the Jaunty installer, but I think they removed it.

---

### Post by Rasa1111 on 2010-09-16
just for s&g's, 
here is a shot of GParted~

 If I simply right click on the 7.51 GB partition, it gives the option to "delete"
If I did that, would it give all the space that was taken up by it, back to the 27.81 GB part.? 

I know I said I should quit, but i hate doing that. 
however, it's probably what ill end up doing.
freekin hate when I dont understand something. 
something that is seemingly supposed to be quite simple. gahhh. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169687&stc=1&d=1284677114[/IMG]

---

### Post by wilee-nilee on 2010-09-16
Your doing fine individuation is a lifelong task, never actually reached but worth the effort.;)

So with gparted showing now you can just delete that sda6 partion and the swap next to it=sda7, and just put a ext4 back in that space and use the custom install to that partition made. You will have to do this from a live cd. You will have to turn off all the swaps to do anything.

Remember as well that you can open gparted at any time during the install to confirm partition #'s and such.

If the swap that is left needs to be adjusted in size you can just delete it as well and make that ext4 in the extended and leave enough room for your new swap sized to your needs.

---

### Post by uRock on 2010-09-16
If you are deleting sda6&7, then you can use the manual partitioner to install in the free space. Using the installer, I would create a 4GB / partition and use the rest for a /home. It will automatically use the swap when doing it this way.

---

### Post by Rasa1111 on 2010-09-16
Thanks for your patience, mates. <3


Ok, .. so...
 1st) What I get (i think i get) lol

Delete sda6 and sda 7, (using Gparted) correct?

Once that is done,  the partition will still be there, but it will now be empty? yeah? 
or no?   

 and/Or,  uhm.. Once that is done, how do I Put an ext4 back in it's place?
Im not sure how to do that?

 Is it siimply a matter of clicking "format", and then just choosing "ext4" ? 

I also dont know how to "turn off swaps? 
to be perfectly honest, Im not even positive as to what the 'swaps' are actually for? lol
*hides face*

Ok, So,  (sorry, please bare with me) lol

(using the liveCD)

Theoretically~ [assuming I have already figured out how to "turn swap off"]
1.I have deleted sda7 and sda7, right?  
(which does what.., leaves them there, but now they are empty?)

2. and I have also created an 'ext4' now, in the partition that was 10.10,  right? (Gparted)  

anythng else there?

 then,  all i have to do, is click 'install', 
use the manual partitioner in 10.10, and tell it to install on the now "empty" ext4 partition? 


One last thing, ,
 What I dont get...

I am confused by this~ 
> I would create a 4GB / partition and use the rest for a /home. It will automatically use the swap when doing it this way.

can you please simplify this as much as possible?  lol :/

The way things have gone in Ubuntu since Ive been using it 
(9-10 months)... from my experience..
 this is probably much easier to do (and understand) than I am making it out to be. lol, Sorry. 


Thanks so much...
and again, apologies for seeming like such a n00b. 
(it's because i am) :-?  :twisted:   lol   <3

---

### Post by uRock on 2010-09-16
I do not blame you for wanting to make sure you have it planned out right. Partitioning can be tricky and getting to click happy can cause you to loose data.

That said you can do all of the partitioning via the installer.

Boot the LiveCD, hit any key at the very first screen so that you can go directly into the installer. This will prevent swap from being mounted. 

Work your way through the installer until you get to the partitioner.

When the partitioner comes up choose the manual mode. My screenshots will walk you through this as much as I can.

Delete your unwanted partitions. Check out the two screenshots of deleting the partitions, mine are not the same as yours, but the concept is the same.

Next click on the "free space" and create the / and /home partitions. Again I have screenshots. The size you use will be slightly different. (Mine say Primary, but your partitions will be logical, because they are in the extended partition.)

You should now see two new partitions that have / and /home by them. Don't worry about creating a new swap. The one you left will be used by the new install as well as the 10.04 that you already have installed.

My last screenshot shows the two partitions will be formatted, yours will also list that it is formatting the swap partition, don't worry, this is normal.

Go ahead with the rest of the install and enjoy your new install.

If you have more questions before going ahead, then feel free to ask.

PS, I am adding another post to place the rest of the screenshots as the UF only allows 5 per post.

---

### Post by wilee-nilee on 2010-09-16
> **Rasa1111 said:**
> Thanks for your patience, mates. <3


Ok, .. so...
 1st) What I get (i think i get) lol

Delete sda6 and sda 7, (using Gparted) correct?
[B]
yes[/B]

Once that is done,  the partition will still be there, but it will now be empty? yeah? 
or no? 

**What you will have is the extended still there that is where the ext4 goes as a logical. ** 

 and/Or,  uhm.. Once that is done, how do I Put an ext4 back in it's place?
Im not sure how to do that?

 Is it siimply a matter of clicking "format", and then just choosing "ext4" ? 

**Yes**

I also dont know how to "turn off swaps? 
to be perfectly honest, Im not even positive as to what the 'swaps' are actually for? lol
*hides face*

**Right click on the swap partition and click swap off**

Ok, So,  (sorry, please bare with me) lol

(using the liveCD)

Theoretically~ [assuming I have already figured out how to "turn swap off"]
1.I have deleted sda7 and sda7, right?  
(which does what.., leaves them there, but now they are empty?)

**At this point you would only have the one last swap left, so in the free space inside that extended partition you create that ext4=logical partition**

2. and I have also created an 'ext4' now, in the partition that was 10.10,  right? (Gparted)  

anythng else there?

 then,  all i have to do, is click 'install', 
use the manual partitioner in 10.10, and tell it to install on the now "empty" ext4 partition? 

**Yes**

One last thing, ,
 What I dont get...

I am confused by this~ 
I would create a 4GB / partition and use the rest for a /home. It will automatically use the swap when doing it this way. 

[B]
Some users like to have a seperate home partition to have in place unchanged to keep their stuff when upgrading or changing distros. Personally I have never found this useful for me, but it is for many others. You would need uRock's help on this area or another who knows this area. Post 15 sort of shows this.[/B]

can you please simplify this as much as possible?  lol :/

The way things have gone in Ubuntu since Ive been using it 
(9-10 months)... from my experience..
 this is probably much easier to do (and understand) than I am making it out to be. lol, Sorry. 


Thanks so much...
and again, apologies for seeming like such a n00b. 
(it's because i am) :-?  :twisted:   lol   <3

I have never tried to figure out the cherrypicking answer schema all my answers are in bold.

Instead of all of this, you could just delete everything but sda1 and just install Maverick in the free space and have the same thing we are trying to do with preformatting.

I would just go this route actually and use a thumb to practice partitoning and installing, thats how I learned basically. A 8 gig thumb or even a 4 gig will take a full install of Ubuntu, and you can bork it to your hearts content while learning. If you do a full install to a external though, you have to make sure grub is pointed at the externals mbr. Up to Maverick grub placement was controlled in the last install window, the advanced button. In Maverick this choice is right in with the partitoning portion of the install, at the lower portion of the gui.

---

### Post by uRock on 2010-09-16
And here are the rest of the screenshots.

---

### Post by wilee-nilee on 2010-09-16
> **uRock said:**
> And here are the rest of the screenshots.

I was hoping you would show back up if the OP wants to have separate home, and of course you started out helping them.

Hey and congrats on the hierarchal jump, now get to them infractions.;)

---

### Post by uRock on 2010-09-16
> **wilee-nilee said:**
> I was hoping you would show back up if the OP wants to have separate home, and of course you started out helping them.

Hey and congrats on the hierarchal jump, now get to them infractions.;)
Lol, thanks. I like playing with partitions. I used Partition Magic to destroy my Windows installs before learning of the world of Linux. Backups are a must.

---

### Post by wilee-nilee on 2010-09-16
> **uRock said:**
> Lol, thanks. I like playing with partitions. I used Partition Magic to destroy my Windows installs before learning of the world of Linux. Backups are a must.

It took me two years of using Linux before I even did a custom partition install, to scared, now it is the only way I go, mainly to keep the swap to the correct size. I have gotten used to using about 4 different partition managers, including partmajic, disc manager (windows), partition wizard and gparted they all have their uses.

---

### Post by Rasa1111 on 2010-09-16
wow! Thanks soo much! 
That should be perfect! :D
Between the two of you...
if I still can't manage it after this... 
My issues got some issues! lol :lol:  

great screenshots and instructions,  dudes!  lol :)

Thanks uRock! <3
Thanks wilee! <3

 I do have one last question before I fire the liveCD back up..
(surprised?) lol

when creating an (or the first)  ext4,  
in this shot~ [http://ubuntuforums.org/attachment.php?attachmentid=169701&d=1284689582](http://ubuntuforums.org/attachment.php?attachmentid=169701&d=1284689582)

 what exactly does the "/" mean? 
( i feel thats a dumb Q that i probably know the answer to), but please pacify me anyway? lol

and, Ive also read (a little) about the separate partitions for /home.
If I didnt want that, I could simply skip that step right?

I just don't foresee myself ever using it, nor am I really sure how I would use it. 

according to wilee, it is a step I dont *have* to take, right? 

Plus my main hdd is only 40GB, so to get all the space I can out of it, would be preferable. 

 I do have a 1TB external, and 250GB external, 
So I guess im not really "low" on space. 
But If I will never use it, [/home partition] 
it will just take up space that just sits there,
which is kinda pointless right?

 i mean, unless there is *another* good reason 
(besides the one wilee gave)to have one that Im unaware of,
but from wilees statement, it doesnt sound like something I would use.

So I would just simply create the / ext4 partition, 
and that's where I put 10.10. 

 Basically just omitting the part where I create the ext4 /home partition. 

 am I golden?  :lol:

 Really, you guys do rock! 
many, many thanks! <3

---

### Post by uRock on 2010-09-16
I have never use the / by itself, but that doesn't mean it isn't possible. You could try it and see how it goes, but you may have to start over if it doesn't work out. 

With the / and /home, the / houses all of the root folders(the OS) and the /home has all of the user data.

Using this and splitting the the almost 8GBs you will have after deleting the sda6&7 partitions shouldn't be a problem unless you plan to make it your production OS. Either way you are using the same amount of space.

---

### Post by Rasa1111 on 2010-09-16
Ok cool, I'll just do it your way then. ;) lol
I trust you. lol

for clarity...
Once i have a /home partition...
Will I have to do anything "special" or out of the 'ordinary' to access it?  Or to access my "home" folder? from either distro? 

Or is it just something that I can "forget about" and it will "be used" automatically? 

Does everything from both home folders (10.04, and 10.10), go to this /home partition? 

 i guess Im just not completely clear as to what it actually does, 
what it's purpose is, 
other than "housing the user data". 

 but yeah, it's really not even enough space to be concerned about, mybad.
__________________________________________________________________________
 
[unrelated rambling]*

and really~ in the end~ (when 10.10 is released on 10/10/10) lol
or shortly after,  I think my plan is to just do a full install of 10.10,
on the whole disk. 

 mainly because I cannot use two of the programs that I thrive on , in Lucid (GIMP, and Stellarium).
 GIMP works, but it's settings went funky and nothing ive done has returned them back to normal, But in 10.10, it's all back to normal. 
and Stellarium works again.
 9.10, stellarium worked fine, 10.04, wont work, 10.10, works great again.
But i often need it for work related things. 
So just that alone, would be a good reason to go to 10.10 for me. lol

 Ok, getting out of here finally to fire up liveCD. :D

Can't thank you enough. <3 
thank you~for your humility, 
thank you~for your time, 
and thank you~ for your patience.. 
:) lol

---

### Post by uRock on 2010-09-16
You will not notice a difference with the two partitions as compared to having just one partition. I use the /home so that I can reinstall the OS without copying all my data to and from external media.

---

### Post by wilee-nilee on 2010-09-16
I say go for the separate home at the least this is a good learning situation and if you don't feel you need it later on you can go a different route. I think you will like it though the idea makes total sense.

---

### Post by Rasa1111 on 2010-09-17
Ok, thanks.

when creating the "/" ext4 partition,
Do I want to choose "primary" or "logical"?
What is the difference? 

 last time i opened it, it was set on "primary",
but i just opened it again, and "logical" was checked,
So which one?

last thing, If I didnt have a /home partition before, 
why would it prevent this from working if I dont have one now?

 right now, if I split up the 8 GB I have, only 4 will be for 10.10? and the other 4 for /home?

still confused I guess, Im sorry. :/

---

### Post by uRock on 2010-09-17
They are being created in an Extended partition, so they have to be Logical.

---

### Post by Rasa1111 on 2010-09-17
ok cool. 

I edited my last post,
Can I squeeze one more answer from ya? lol
man you must really think Im a "tard" eh? lol

> last thing, If I didnt have a /home partition before, 
why would it prevent this from working if I dont have one now?

 right now, if I split up the 8 GB I have, only 4 will be for 10.10? and the other 4 for /home?

still confused I guess, Im sorry. :/

---

### Post by uRock on 2010-09-17
You made me do something I have never done. Open gparted in a vbox. It shows the single partition install as /. That said, it should work. When you do your next full install you should consider using the /home in case you have to reinstall.

=)

---

### Post by Rasa1111 on 2010-09-17
Thank you bro! :D

 Talking to you live from freshly installed 10.10! woot! \o/  \o/  \o/   :D haha

 Now to boot into my 10.04 install and make sure she is ok! lol ;P

You are beautiful, uRock!
You to wilee!

 I also noticed something "different" about you uRock~
congrats on movin'up the food chain! lol :D
You deserve it mate. <3

Damn, Im happy! lol 
 Praises! :D

---

### Post by Rasa1111 on 2010-09-17
oh boy! 
and to finish, with a big ol' cherry on top~

Now posting to you live from me Lucid install! woot! :lol:

Everything is great!

dammit I love you guys! <3<3<3 

Thanks a million broskys. 
I owe you one! or ten. :D

S.o.l.v.e.d.! lol

 and I can't believe some people actually have the b@11$ to complain about "having" to use the forums to get help/support! wow. lol

I never got such awesome help/support when I was using an OS I had to pay for. 

 :deep bows:, love and blessings.

yoU Rock!

---

