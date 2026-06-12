---
title: "Can't get past install screen (Forward button not working)"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by prowler_ on 2010-10-11
Hi.
I'm installing Ubuntu 10.10 on my desktop and it seems I can't get past the "Who are you?" screen as I can't click the forward button

[IMG]http://imgur.com/bzKyo.png[/IMG]
I've tried a number of times; installing from within live usb, without an Internet connection (Just to see if it helps) but all failed

Sorry if this is a newbie question and thanks in advance.

EDIT: It was because my username had a capital letter in it.
Sorry for the newbie question again

---

### Post by P4man on 2010-10-11
Heh.. well, the lack of green checkmark may have been a hint, but a clear error message wouldnt have hurt here. I wouldnt have spotted it myself.

---

### Post by paulobear on 2010-10-11
> **P4man said:**
> Heh.. well, the lack of green checkmark may have been a hint, but a clear error message wouldnt have hurt here. I wouldnt have spotted it myself.

I had the same issue w/a '.' between my first and last names. Thought it would be nice to copy my Windows user name format since I'm installing in a VirtualBox machine on my Windows 7 Enterprise laptop.

Paul

---

### Post by NCLI on 2010-10-11
I've reported this as a Papercut(A small usability bug) in Launchpad, so hopefully it'll be fixed in time for 11.04.

---

### Post by localmotion on 2010-10-14
Thanks I was having the same issue, so silly, it really should have an X next to it.

---

### Post by aderaidou on 2010-10-22
username cannot start with an UPPERCASE letter.  I had the same problem and it was driving me nuts.  You should get a green arrow checked to the right of the username box once you type a username in the correct format.

---

### Post by Ronananator on 2010-10-30
> **aderaidou said:**
> username cannot start with an UPPERCASE letter.  I had the same problem and it was driving me nuts.  You should get a green arrow checked to the right of the username box once you type a username in the correct format.


I have had this problem aswell but thanks to you it worked i first corrected my name to lower case and then i changes username and the computer name is serprisingly it works thanks a million helped alot

---

### Post by purenrg4life on 2010-10-31
Thanks for helping me with same issue!

---

### Post by darkerlink on 2010-12-01
this was not a newbie question. This has helped me a lot! thanks.:D definitely a paper cut.

---

### Post by Quackers on 2010-12-01
I think I'm right in saying that the username can't end with a capital letter either.

---

### Post by TopherAbe on 2010-12-01
Okay, so, both the machine name and the username can't have a capital letter in their names then?

---

### Post by Quackers on 2010-12-01
The machine name, by default, is generated from the username iirc.

---

### Post by phr0ze on 2011-02-16
Bringing this back because it's still an annoying bug. Seems to be more than a papercut to me. I was completely stuck without google and this thread.

Two things. If we are supposed to look for a checkmark, there isn't one on the password field. And there isn't an error on the user name field. So which is it. If its a check mark, then put one next to password. Still give us an error message though.

Thanks

---

### Post by mörgæs on 2011-02-16
In 11.04 there is a better explanation on this screen.

---

### Post by cdhaggard on 2011-03-31
Ok, so you can't use capital letters in your user name.  I've been having this exact same problem, so thanks for clearing it up.  The installer could be a little more clear on the user name requirements.

---

### Post by BlueBoden on 2011-04-13
I just had this problem as well in 11.04, and I'm certainly no beginner at linux. I was going to use Ubuntu on a server machine, which is to host some of my domains, and this problem halted me for about half an hour (at least), before i figured out what the problem was.

So what is the big deal with this? This might not exactly hit you as constructive criticism of Ubuntu, BUT seriously, come on.. Why can't we use capital letters in the username?
On another matter, why do we HAVE to enter a password if we don't want one? Why is Ubuntu forcing us to enter a password? Thats what annoys me the most at the moment!

I honestly don't see the point with the password thing.. Something goes wrong i just re-install, its really not a big deal if someone gains access. Its far more annoying to get forced to enter crap you won't need.
I easily forget that i chose a different username, because i got so much going on, on a lot of different places. I'll likely have to write my self a note, and keep it attached to the server, to remember that i used lowercase.

Something else relevant to this issue, which seems rather strange, is that Ubuntu seems to be making network connections while installing. This confused me even more, because it seemed like it was still doing something in the background. Than i finally decided to search on google "Ubuntu install cant press forward" (or something like that), and found this post. So unless you are really into all the details, this is something which will confuse people. The only reason i did this, was that it said "ready when you are", which again seems rather ambiguous. It would have been more on target, if it actually said something like "Installation complete. Please fill out the required fields.."

Having that said, Ubuntu is a great OS, because its free. And i will  likely continue to use it regardless of these smaller annoyances.

---

### Post by mörgæs on 2011-04-14
> **BlueBoden said:**
> Why can't we use capital letters in the username?


Because it would be confusing to have John, john and JoHn being three different users on the same machine. 


> **BlueBoden said:**
> 
Something goes wrong i just re-install, its really not a big deal if someone gains access. 

I don't think that most users will agree on this one.


Er du dansker?

---

### Post by Quackers on 2011-04-14
I happen to agree with BlueBoden on the password point.
I don't see why Ubuntu should insist on me using a password. I have no confidential info on my machine. No bank details, no credit card details, nothing. I am the only user of this laptop - there isn't even anybody else here! If I make the choice to not use a password Ubuntu should respect that. By all means warn me that I'm taking my life in my hands, but respect my choice!

With regard to the no capital letters in the username I would say this.
On my first ever installation of Ubuntu I used Mike as a username, but could not progress in the installation. I realised that there was no green tick mark next to the username and wondered why. In less than 60 seconds I figured out why, by trying different things.
It's often safer to assume that you have done something wrong, rather than assuming the system is broken.

---

