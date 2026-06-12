---
title: "Software Center Changes in 16.04"
date: 2017-08-07
forum: Installation &amp; Upgrades
---

### Post by slow-speed on 2017-08-07
Just did a fresh install of 16.04 LTS on another computer, and I found that the Software Center does not look the same or work the same, and the automatic upgrade notification system seems to do nothing.  Even Synaptic has changed for the worse.

What happened?  Is it possible to get it back to the 14.04 look and feel and operation?

---

### Post by ajgreeny on 2017-08-07
I have never used the software-centre and if I want a GUI always go to synaptic.  If you really want the software-centre try a first update in terminal with ```
sudo apt update
sudo apt upgrade
``` and you may find that the software-centre now works properly.

However, I mainly use synaptic and did not notice any changes of great consequence between the version of synaptic in 14.04 and 16.04; what is your problem with the 16.04 version?

---

### Post by slow-speed on 2017-08-07
I just figured out something I should have checked before.  The new  program is entitled "Software", and the old program was named "Ubuntu  Software Center"version 13.10.

[ATTACH=CONFIG]276306[/ATTACH]
This is the new program.


[ATTACH=CONFIG]276307[/ATTACH]
This is the old program.

The old one worked so much better.



I wanted to show the different screens from Synaptic, but this editor won't let me.

---

### Post by vocx on 2017-08-07
> **slow-speed said:**
> I just figured out something I should have checked before.  The new  program is entitled "Software", and the old program was named "Ubuntu  Software Center"version 13.10.
...

You are correct. Basically, at some point before 16.04 Ubuntu decided to use "Gnome software center", simply called Software, instead of the previously available "Ubuntu software center". These changes are not critical to the system but will definitely surprise some users, mostly those who use graphical interfaces a lot.

[http://www.omgubuntu.co.uk/2015/11/the-ubuntu-software-centre-is-being-replace-in-16-04-lts](http://www.omgubuntu.co.uk/2015/11/the-ubuntu-software-centre-is-being-replace-in-16-04-lts)

---

### Post by slow-speed on 2017-08-07
So basically they took a bad program out and put in a worse program.  Now that's thinking.  No one's going to accuse them of being bright.

Damn shame too, since even updates don't work the same.

---

### Post by vocx on 2017-08-08
> **slow-speed said:**
> So basically they took a** bad program** out and put in a** worse program**.  Not that's thinking.  No one's going to accuse them of being bright.

Damn shame too, since even updates don't work the same.
Good, bad, better or worse are all subjective when it comes to software.

I myself don't see any problem with the current "Software" program installed. But I also don't use it often, as I mostly use the command line to install and remove packages. Since it's free software, I think there should be a way to install that particular piece of software if one is really keen to do it.

---

### Post by mastablasta on 2017-08-08
> **slow-speed said:**
> So basically they took a bad program out and put in a worse program.  Not that's thinking.  No one's going to accuse them of being bright.

Damn shame too, since even updates don't work the same.

no they used a default so they do not have to spend time maintaining a similar program. just wait until gnome desktop enters Ubuntu... :P

---

### Post by slow-speed on 2017-08-08
I must be in the military; "hurry up and wait". ;)

But seriously, I like it when the updates show up on the task bar area and all the user needs to do is select that and select to install.  That does not appear to be so doing, any longer.  In that regard, the old one is clearly better.

The way it all appears to work is that there is the underlying updating and installation routine.  Then the software of choice runs on top of that and creates the user interface.  Obviously, most people do not use Ubuntu or any other Linux distro to run the command line, so the real issue here is the intuitive graphical nature of the beast, and that is upon which I am focusing.

Along the same lines, I also had a problem with Synaptic, which I prefer to use over the other silliness.  Its interface has changed for the worse making it less intuitive, and I cannot see why that needs to be either.  Is that just another unnecessary change that Ubuntu decided to make?

There are some serious and provable changes which clearly affect usability, and that needn't be the way they are.

Thanks for everyone's thoughts.  I just wish there was a fix.

---

### Post by ajgreeny on 2017-08-08
> I also had a problem with Synaptic, which I prefer to use over the other silliness. Its interface has changed for the worse making it less intuitive, and I cannot see why that needs to be either. 
I will ask again; what are those changes that you don't like.  I have been using synaptic for many years, since I began using Ubuntu in 2005, and the changes I see are very small.

I wonder if I make changes in the Preferences that make it look just about the same as it always has.  Do you leave it at the default look and behaviour?

---

### Post by slow-speed on 2017-08-08
AJGreeny, yes, like i mentioned before, I was unable to upload the other  comparison pics, but I will try again now.  Let's see if this works......



.........Nope, still won't work.

---

### Post by vasa1 on 2017-08-08
I've jailed a couple of posts in this thread. Let's play nice. Please read our [Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules").

From there:> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.and> Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them.

---

### Post by mastablasta on 2017-08-09
> **slow-speed said:**
> I must be in the military; "hurry up and wait". ;)

But seriously, I like it when the updates show up on the task bar area and all the user needs to do is select that and select to install.  That does not appear to be so doing, any longer.  In that regard, the old one is clearly better.
wow that really is not good. is that by design or a bug on your install? 

not having that feature would bother me as well.

> 
Along the same lines, I also had a problem with Synaptic, which I prefer to use over the other silliness.  Its interface has changed for the worse making it less intuitive, and I cannot see why that needs to be either.  Is that just another unnecessary change that Ubuntu decided to make?

There are some serious and provable changes which clearly affect usability, and that needn't be the way they are.



i glanced thorough synaptics web page and i can't see any major difference mentioned. other than minor improvements and bug fixes.

---

### Post by slow-speed on 2017-08-09
Thanks, MastaBlasta, that was part of my point. I just wish others would get that.

This happens in a fresh install on a system that was running Vista.  The install did everything and was allowed to use the whole drive and format as it wanted.  There seemed to be no problem during that process and all finished well.  Abiword was removed and Apache OpenOffice was installed.  With no other user changes, I can see no reason for the difference between Xubuntu 14 and 16.  It just makes no sense.

Now, if you or Vasa1 can tell me how to get the image attachment mechanism to work correctly on this forum, I could show the difference between the Synaptic versions.  (Frankly, I am _not_ convinced it is a Synaptic problem.)  I have five pictures uploaded and you can see I've used two, and while it states that unused files will be removed within an hour, it has been two days and they are still there and blocking me from uploading the one I want.  Putting them in another directory does not work, even though it allows such creation.  Go figure.

---

### Post by vasa1 on 2017-08-09
> **slow-speed said:**
> ...

Now, if you or Vasa1 can tell me how to get the image attachment mechanism to work correctly on this forum, I could show the difference between the Synaptic versions. ...
What happens when you click the little paper clip icon just above the posting area? If it doesn't work, is it possible you have some sort of script blocker active?

---

### Post by slow-speed on 2017-08-10
Yes, that is what I'm using and it does allow me to go thru all the convoluted steps to upload files.  You will notice that it worked to get the first two posted in this thread.  (Pop up blocking will stop that one, but the lower "Manage Attachments" feature works exactly the same and appears to be not blockable.)

But the issue is as I pointed out.  It only allows a set number of files (5) and does not have a way to remove unwanted ones and replace with those wanted, nor does it automatically remove them in the time frame stated.

What this does is paralyse the user from further screenshot uploads.

Does anyone know why?  I can no longer continue the other part of the original reason for this thread without this ability. 

 (It might be well to note that other forum software has not such limitation.)

---

### Post by vasa1 on 2017-08-10
> **slow-speed said:**
> Yes, that is what I'm using and it does allow me to go thru all the convoluted steps to upload files.  You will notice that it worked to get the first two posted in this thread.  (Pop up blocking will stop that one, but the lower "Manage Attachments" feature works exactly the same and appears to be not blockable.)

But the issue is as I pointed out.  It only allows a set number of files (5) and does not have a way to remove unwanted ones and replace with those wanted, nor does it automatically remove them in the time frame stated.

What this does is paralyse the user from further screenshot uploads.

Does anyone know why?  I can no longer continue the other part of the original reason for this thread without this ability. 

 (It might be well to note that other forum software has not such limitation.)May I suggest you open a thread in [Forum Feedback & Help]("https://ubuntuforums.org/forumdisplay.php?f=48") on this problem?

---

### Post by slow-speed on 2017-08-10
Okay, be glad to.  If that can be fixed, we can revisit this later.

---

### Post by QIII on 2017-08-10
Your are limited to 5 images as a result of the software used by the forums.  We have no control over that.  Canonical provides the software and the servers.

You are likely having issues removing/replacing images because you need to click Edit Post --> Go Advanced to make that sort of modification.

---

### Post by slow-speed on 2017-08-10
Thanks, but to what modification are you referring?

---

### Post by vasa1 on 2017-08-10
> **slow-speed said:**
> Thanks, but to what modification are you referring?
Maybe this:> But the issue is as I pointed out. It only allows a set number of files (5) and does not have a way to remove unwanted ones and replace with those wanted, nor does it automatically remove them in the time frame stated.
which is what you wrote earlier.

---

### Post by slow-speed on 2017-08-10
Perhaps, but it makes no sense since I made no modifications nor do I  see where that could be done.  Further, the implication is that one can  fix the problem by going back and editing the post?

Also, to be clear, I don't use quick reply; I almost always use reply to thread.

---

### Post by vasa1 on 2017-08-10
Simple question: can you make a post and include just two images of synaptic package manager to illustrate what you feel is different between versions?

Rest assured that the forum's attachment facility is working at least for this trivial task of uploading two images.

---

### Post by QIII on 2017-08-10
> the implication is that one can fix the problem by going back and editing the post?

Yes. 

Again:  If you want to modify your post by adding or deleting images, go to **Edit Post** and then to **Go Advanced**.

There is nothing paralyzing you.  You are limited, however, to five images -- we can do nothing about that.

---

### Post by slow-speed on 2017-08-11
QIII,
This is a new post.






This is an edit.  Still no way to add another file, and all old files are still there and paralysing the system.

Got it?

---

### Post by ajgreeny on 2017-08-11
So what is it that you don't like and has changed in synaptic that you show in your pic?

To me it looks just as it has for many years, and certainly no obvious change that I can see since 12.04.

---

### Post by slow-speed on 2017-08-11
Mainly, that the interface no longer has a built-in search box which reacts as one types in by displaying possible matches below.  Now it is a pop-up window that is no longer part of the main app.  This is exactly like Software does and is demonstrably not as useful as before.

---

### Post by ajgreeny on 2017-08-11
Ah, OK!

I admit I had not even noticed that the "Quick search" filter had gone, mainly because I never used it.  I normally search by "Name only" in synaptic and always found the separate search dialogue more accurate and useful.

However, it looks as if you can get Quick Search back by installing the **apt-xapian-index** package which is no longer a default.
This is an answer direct from [https://askubuntu.com/questions/763857/how-to-get-quick-filter-back-in-synaptic-ubuntu-16-04](https://askubuntu.com/questions/763857/how-to-get-quick-filter-back-in-synaptic-ubuntu-16-04) which I have not tested.

EDIT:
Tried the solution to restore Quick Search, and it certainly works, though as I say, I am unlikely to use it very often.

---

### Post by slow-speed on 2017-08-11
WooHoo!!!!!

Dude, you figured it out.  Outstanding!

The upgrade went without a hitch, and the program came up as it should.

So, we have fixed two things; Synaptic works like in 14 and we can ignore Software.  There are always a lot of people suggesting Synaptic anyway in all version of *ubuntu, so I have no trouble recommending it as well.

That leaves the concern about upgrade notifications.  I'm going to give it a few days and see if we notice anything popping up about that.  Surely there should be an update within a week or so.  When I know more, I will post back here.

ajgreeny, you are awesome.  :D  Thank you for the fine help and great solution.  Many thumbs up!!!!

---

### Post by slow-speed on 2017-08-15
Just found out that the pop-up notification for available updates is still _not_ working, so I will have to do some research to find out why that automatic function does not work in 16.

---

