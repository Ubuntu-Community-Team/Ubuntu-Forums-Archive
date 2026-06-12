---
title: "removing that oh so annoying SUDO!!! _HOWTO"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by Slaskpelle on 2006-09-06
Hi Peeps,

Do you get tired of always having to type "sudo" before installing anything? I know i do! Also how annoying is not being able to log in your desktop as a ROOT. Well here's a "POWER USERS" howto.

If you'd like to also become a "POWER USER" follow these simple, simple instructions.

OK! 

(1) Get yourself logged into your UBUNTU (with a boring user name, don't worry this will the last time you'll have to do this! ](*,) )

(2) Type  'sudo init 1' 

(3) Enter your password

(4) (Yippee we are nearly ROOT!)

(5) Type 'passwd'

(6) Now enter a password. (this will be your new "ROOT" pass)

(7) Hey now cool rockin daddy, your now a SUPERUSER like me! :twisted:  How does it feel? Soooo Naughty!!

I hope people find my howto helpful, any improvements to it are most welcome and may appear on my new "HOWTO" website im currently building.

Next "HOWTO" Post:

Clearing up the fatty ubuntu headgehog with "rm -fvr" command..

---

### Post by pyros on 2006-09-06
Does this mean that I can log in under my normal user name and I won't have to keep entering my password, or will I have to log in as root?

---

### Post by Slaskpelle on 2006-09-06
No no no,

Do this and you can simply use "ROOT" (far more powerful functions etc.)

But be careful, if you don't powerful enough then don't go there dawg. 

"Danger will robinson!"

---

### Post by bluenova on 2006-09-06
I always use:

sudo -i

if I have lots to do. That gives you a root prompt.
root@mybox$

---

### Post by Slaskpelle on 2006-09-06
Good tip. Lets keep the posts flowing.

Your going on my howto thanks

XX

---

### Post by chinaski on 2006-09-06
but don't they say it's not a good idea to log in as root abitually?

---

### Post by skymt on 2006-09-06
Please see my comment in the [duplicate thread](http://www.ubuntuforums.org/showthread.php?t=252107).

Slaskpelle, I don't mind the end result of your HOWTO. Running as root has advantages, as well as disadvantages. However, you made it much more complex than it needed to be. 'sudo passwd' in a terminal gives the same result, enabling the root account.

---

### Post by pyros on 2006-09-06
Absolutely. But then I have everything I care about in my home partition, and it doesn't take any effort for me to reinstall if I really hose something. Which I tend to do anyway. I'd just rather not use an account named "root"

---

### Post by whizbaby on 2006-09-06
There are situations where you actually NEED a root account, e.g. computers with /home mounted over network. Enabling it is not a great threat (not greater than using su or sudo), **but enabling graphical root login is highly unrecommended, don't do that, you are increasing the vulnerability of your computer by a large amount!**. If you dislike typing passwords all the time install kerberos!

---

### Post by aysiu on 2006-09-06
```
sudo -i
``` and ```
gksudo nautilus
``` will take care of the vast majority of users' root "needs." I've never needed to enable a root account login.

---

### Post by TyphoonJoe on 2006-09-06
Just want to add that most admins (*NIX/VMS/Windows) that have root access do NOT run as root unless necessary.  I know admins that have worked 20+ years in the industry and still are very careful with root.  I expect those that are not careful won't last that long.

It is all too easy to mistype simple commands- so the permissions error on certain commands is a nice reminder to 1- use sudo and 2- stop and think.  The inconvenience of running sudo is minor compared to the things that may occur if always running as root.  

That said, if you have more than a few commands you need to run you can always "sudo bash" or "sudo ksh" to get a root terminal.

---

### Post by Slaskpelle on 2006-09-07
Yes, you are very right indeed TyphoonJoe. 
Though the truth is that many people like me just prefer to work with a root/GUI for comfort purposes. 
Like so many other powerusers, i like the feel of the good ol' "mouse-click 'o' icon" rather than really basic and archaïque terminals. (pardon my french but I feel good quoting french words)
We have progressed a long way since the days of Unix, and god bless we never go back there! 

I'm in love with Ubuntu but I believe It has to work more in the way of Microsoft Windows 98:KS  (still the most popular version) in order for it to progress out to the commercial market. 

Just my 50 cent 8)

---

### Post by whizbaby on 2006-09-07
Again, you're replacing security with 'good feel'.
And to the terminal-phobia:
Why do people think it's more comfortable clicking and dragging around like in a game instead of using words and language (mankind developed that for thousands of years) to communicate with the machine?

---

### Post by Lord Illidan on 2006-09-07
> **Slaskpelle said:**
> Yes, you are very right indeed TyphoonJoe. 
Though the truth is that many people like me just prefer to work with a root/GUI for comfort purposes. 
Like so many other powerusers, i like the feel of the good ol' "mouse-click 'o' icon" rather than really basic and archaïque terminals. (pardon my french but I feel good quoting french words)
We have progressed a long way since the days of Unix, and god bless we never go back there! 

I'm in love with Ubuntu but I believe It has to work more in the way of Microsoft Windows 98:KS  (still the most popular version) in order for it to progress out to the commercial market. 

Just my 50 cent 8)

I don't agree with you.

Lots of the causes why people destroy a working system is when they are always administrator. 
Sure, if they know what they are doing, fine. But what if they don't? Like when they decide to clear their Windows folder because it is too big? Or meddle around in the registry to speed up?

Sudo works fine.

---

### Post by Slaskpelle on 2006-09-07
Please keep this discussion on linux please lord. Lets not get into  "Micro$oft Windoze" here. [-( 

Anyway...

"with language comes the ability to curse and swear, and that's exactly what the simplistic terminal is all about, a curse, or perhaps just lazy programming? Microsoft Windows ditched the Dos prompt, isn't it time for Linux to take a similar step? Also, Like Jim Morrison i like "good feel", i Wanna get my mouse K(L)icks whilst im still alive and kicking.

Regarding "sudo" (i cant believe it, my howto enabled you to remove 'sudo', i and here i am STILL typing sudo (LOL!)

I hate having to press "backspace" "backspace" "backspace" "backspace" etc... when typing a command, just because i've forgotten to type "sudo".

I understand Ubuntu is a fork from debian, and is based more for the "green behind the ear" linux user, but please.. "are we not men?"

---

### Post by whizbaby on 2006-09-07
> **Slaskpelle said:**
>  a curse, or perhaps just lazy programming? Microsoft Windows ditched the Dos prompt, isn't it time for Linux to take a similar step?

**Hell, NO!** There are a lot of administrative tasks that can only be done correctly via terminal. Without using it you will never understand it's power(besides in hastalavista there will be a *new* M$ command line, guess why.) Did I already mention that graphical interfaces present a threat to system security? Shure I did !(now think of M$ again)
(and what is this 'lazy programming'-talk)
> 
I hate having to press "backspace" "backspace" "backspace" "backspace" etc... when typing a command, just because i've forgotten to type "sudo".

Type 'ctrl-a' to jump to the beginning of a line.(that's exactly what I mean with learn to use it: learn how it's supposed to be used. Or do you think thousands of administrators are unhappy with the shell?)
here some additional 'jumping'
ctrl-e end of line
alt-f  next word
alt-b  last word
alt-d  delete from cursor position to end of word
ctrl-k delete from cursor position to end of line
tab  auto command and path completion

---

### Post by The_Apprentice on 2006-09-07
It would be nice to have a pugin that prompts you for credentials when you try and do something in the GUI, much like the Package Manager does.

If I want to create a directory, it is becuase I want to create a directory.
I can not even change the permissions via the GUI.
I do not want to go on a swear fest and then decide it is "easier" to fire up a terminal session and sudo create it there.
It totally defeats the object of having a GUI.

I mainly use my box as a server, though as it is permenantly on I use Firefox and Evolution for quick checks on things.

I want to try and do things properly as I am trying to "learn" Linux from a professional viewpoint.

I guess the move I get used to CLI commands (I was brought up on DOS) and Linux concepts then the less frustrating it will be.

---

### Post by Lord Illidan on 2006-09-07
> **Slaskpelle said:**
> Please keep this discussion on linux please lord. Lets not get into  "Micro$oft Windoze" here. [-( 

I quoted an example from Microsoft Windows because that is a good example why not to use Administrator all the time, or root all the time.

> Anyway...

"with language comes the ability to curse and swear, and that's exactly what the simplistic terminal is all about, a curse, or perhaps just lazy programming? Microsoft Windows ditched the Dos prompt, isn't it time for Linux to take a similar step? Also, Like Jim Morrison i like "good feel", i Wanna get my mouse K(L)icks whilst im still alive and kicking.

Regarding "sudo" (i cant believe it, my howto enabled you to remove 'sudo', i and here i am STILL typing sudo (LOL!)

I hate having to press "backspace" "backspace" "backspace" "backspace" etc... when typing a command, just because i've forgotten to type "sudo".

I understand Ubuntu is a fork from debian, and is based more for the "green behind the ear" linux user, but please.. "are we not men?"

1.If you think that CLI is behind the times or useless, you are seriously mistaken.
2. Sudo and gksudo can be used to do a lot of tasks you used to do when in root.
3. This howto is potentially dangerous.

---

### Post by Slaskpelle on 2006-09-07
Wizzway, 

Thanks for the good info, these tips really help. 

I guess my HOWTO needs revision? I'd like to thank you all for contributing to this thread.

To be honest i've only been using ubuntu for a few days now,as i come from the "LINDOWS-OS" side of town.

I'm think now im pretty advanced with ubuntu (easy) i'll try downloading the amd64 port of Debian sarge. 

My rig its pretty meaty, lots of disk space, good enough mem (2x 512 PC2100 and 1x 256 PC2700) and a Athlon XP2500 sits behind the wheel. (Bios tweek'd for performance) 

Thank you all for the help! Happy Hacking!

---

### Post by Druidor on 2006-09-07
Think this is a very dangerous thing being root all the time.

Beeing a noob to linux The ability to make a dire cockup would be greatly increased without the ever present password prompt.

Hey if I wanted windows worries I would still be using it with rubbish being installed left right & centre.

I will stick with the sudo & gksudo nautilus & be prompted when I am about to do something that is possibly half arsed.

---

### Post by xpod on 2006-09-07
> To be honest i've only been using ubuntu for a few days now,

WOW......and theres ME still asking "why for"...."where to"...."and how the F**K"   after 3 whole weeks.

Still i dont think i`ll be following this "how to".

After 2 weeks on windows i learned NOT to use my "administrator account" for
most things.....email,web etc.

That was 6 months ago and now im here i certainly dont want to UNlearn all i have learned......i`ll stick to being a "sudo i.t expert";)

---

### Post by yopnono on 2006-09-07
> I hate having to press "backspace" "backspace" "backspace" "backspace" etc... when typing a command, just because i've forgotten to type "sudo".

Or you can easily just press the *home* button that will also bring you to the beginning of the line.

I also forget to type sudo sometimes.

---

### Post by jimcooncat on 2006-09-07
I do appreciate the little extra protection against bonehead mistakes that sudo gives me. Plus I'm starting to store stuff on my machine, and share it with other users, so the data's becoming important -- and not all mine.

But I've got so used to typing "sudo" that it flies off my fingers so fast I'm not sure the "bonehead protection" is going to work as well as in the past. Hopefully, I'm learning good practices so I don't need so much protection, now that typing that word has become reflex.

I must be the only old crank around that keeps a command-line console open on my Windows machines... 

I see a lot of explanations for using sudo based on the idea that a malicious program only has rights to affect the data available to the user it runs as. If you have an easy-to-reinstall machine with only your own stuff on it, somehow that explanation doesn't seem so attractive. It's like the priorities are backwards -- the machine's not more important than my own data!

I wouldn't mind seeing the separation ideas expanded to make it simple to run some "target" programs (firefox, flash, streamtuner, thunderbird) as a separate user with minimal rights. But of course the environment would have to be set up to make it easy to save files and be able to work with them.

---

### Post by blackened on 2006-09-07
> "with language comes the ability to curse and swear, and that's exactly what the simplistic terminal is all about, a curse, or perhaps just lazy programming? Microsoft Windows ditched the Dos prompt, isn't it time for Linux to take a similar step?

You're comparing apples to oranges here. Or, for a better analogy, you're comparing an All-But-Dissertation to a preschooler. The Linux command line is exponentially more useful and powerful than the dos prompt could ever imagine to be. Not to say the dos prompt isn't useful, but in Windows everything was so purposefully dumbed-down that anyone who knew how to type *cd /w* believed themselves to be the most L33t "poweruser" in the history of computing.

I have no personal agenda as far as Linux is concerned. You always see these "Is linux ready for the desktop?" and "Is this the year linux will gain majority market share?" threads that are oh so annoying. Personally I don't think it really matters whether the answer to either of those questions is yes or no. As long as the mission stays the same with the emphasis on quality and security, then does it really matter how many people use it?

As a self-proclaimed "poweruser" you should understand that everything that can be done via graphical login can be done via the command line. If you find the command line annoying and choose not to use it, then you ignore an integral part of the operating system. It doesn't matter what h4rdc0re distro you use, if you lack the essential knowledge, then it's all just for "I got distro-x installed on my data-smokin piece of machinated love balloon" bragging rights which are superficial and insignificant.

And to get my post back on-topic: The choice to use sudo over root login in Ubuntu was not an arbitrary decision by the devs. You are no less an administrator whether logged in as root or issuing commands via sudo. Granted it is quite a bit easier to issue a series of commands without preceeding each with sudo, but that's where sudo -i comes in. Couple stupidity (or sheer lack of experience) with arrogance and/or zeal, and you have serious problems in your future. "It is decidedly so" says the magic 8-ball.

---

### Post by Slaskpelle on 2006-09-07
don't be a jealously custard!

---

### Post by aysiu on 2006-09-07
Saying the terminal is simplistic compared to the GUI is like saying the ability to say "I have to go to the toilet" is simplistic compared to crossing your legs, jumping up and down, and pointing at your crotch.

---

### Post by Slaskpelle on 2006-09-07
> **aysiu said:**
> Saying the terminal is simplistic compared to the GUI is like saying the ability to say "I have to go to the toilet" is simplistic compared to crossing your legs, jumping up and down, and pointing at your crotch.

Please keep to the subject, I don't think the Forum admins like toilet humour. 
To be honest I really don't get what you mean by your quote, a GUI has 16m colours plus, resolutions as high as you want and all the added extras whilst a terminal only has black and white (or a few more boring colours if you have tweaked your kernel). 
So tell me now a terminal isn't simplistic? 

Either way, I am currently trying to find a way to change the name of my root account to something else, like "leader" "warchief" or "The_boss" but I might have to start that up in a different thread?

Teh only purpose of this howto was to teach other powerusers like me how to get past that horrible sudo thing. Filthy Kitten

---

### Post by cstudent on 2006-09-07
> **Slaskpelle said:**
> 
Teh only purpose of this howto was to teach other powerusers like me how to get past that horrible sudo thing. Filthy Kitten

I wouldn't classify you as a power user. A Linux power user understands the purpose of sudo and knows the strength of the command line.

---

### Post by Slaskpelle on 2006-09-07
Regardless of your personal oppinion, most of my friends do consider me a power user so it isn't just something I say to seem "cool dude". 
Also, if it wasn't due to all the lazy programing and conservative views going on out there in our community, the Linux GUI would be just as potent as the terminal by now.
I think this thread should be closed and perhaps made a sticky to help other people in my situation. 

And as a final 50 cent, a quote from the Scorpions hit song Winds of Change (which sums up how i feel about Linux's future" 

The world is closing in
Did you ever think
That we could be so close, like brothers
The future's in the air
I can feel it everywhere
Blowing with the wind of change
Take me to the magic of the moment
On a glory night
Where the children of tomorrow dream away
in the wind of change

---

### Post by cstudent on 2006-09-07
Well, make sure you give out your email address so all the people that trash their systems because of your poor advice can get a hold of you for help.

---

### Post by Slaskpelle on 2006-09-07
Sorry I have been away for a while, i had to reinstall, like a knights templar of christ. 
How do you get your .deb file "sportstracker" to work, my system crashed (my memory dimms broke) when i tried to run it, is it a Linux virus? perhaps you should give me your email address, because i honestly never seen a program physically break a dimm slot before.

---

### Post by bluenova on 2006-09-07
Post removed by owner.

---

### Post by aysiu on 2006-09-07
I don't see why this has become a command-line v. GUI thing.

*sudo* is for the command-line.
*gksudo* and *kdesu* are for the GUI.

**There's absolutely no reason you have to log in as root**, either graphically or in the terminal. If you feel the need to make root changes graphically, create a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` or ```
kdesu konqueror
``` and you're set. No need to log in as root.

---

### Post by whizbaby on 2006-09-07
> **Slaskpelle said:**
> GUI has 16m colours plus, resolutions as high as you want and all the added extras whilst a terminal only has black and white (or a few more boring colours if you have tweaked your kernel). 
So tell me now a terminal isn't simplistic? 

We were not talking about the look of course.
Do you think *power over computer* is linearly dependant from *colours on display*?
> 
Either way, I am currently trying to find a way to change the name of my root account to something else, like "leader" "warchief" or "The_boss" but I might have to start that up in a different thread?

You could do that, if you want ([COLOR="Red"]I reject all responsibility for that, never did it, don't know about arising problems. Don't do that without being **ABSOLUTELY** shure about **ALL** the consequences[/COLOR])

**sudo usermod -l root**

(compare with what you would have to do in GUI)

---

### Post by Slaskpelle on 2006-09-07
I tried gentoo and slack, but the people in the forums weren't as nice (and the reception to my kernel include ideas went down like a lead  zeppelin!). 

I feel really at home here in the Ubuntu (humanity to others etc..) community. In fact i think guys.. im hear for the duration.

Lets make a human daisy chain (see ubuntus frontpage for "howto") and dance around the linux maypole of peace.

Peace, Love and Unix

---

### Post by aysiu on 2006-09-07
Yes, the terminal is *visually* simplistic, but it is *functionally* sophisticated, just as a book is *visually* simplistic--being just black ink on white paper. Books can be quite sophisticated, though, and convey emotion, story, tension, arguments, statistics...

---

### Post by BLTicklemonster on 2006-09-07
> **whizbaby said:**
> 
Why do people think it's more comfortable clicking and dragging around like in a game instead of using words and language (mankind developed that for thousands of years) to communicate with the machine?

You are joking, right?

---

### Post by whizbaby on 2006-09-07
removed(posted twice, forum is slow sometimes, is it?)

---

### Post by whizbaby on 2006-09-07
What do you mean *joking*?
All I say (perhaps too compressed) is that *language* (this stuff composed of words) as a medium to communicate is unbeaten. Therefore it's clever to implement some advantages of it into computer<->human communication. (actually on a computer *words* are commands and parameters. You could make sentences with that, not to speak of whole programs). I'm not saying that GUI is senseless, but there are enough situations where it *is*. On today's computers you'll need both to get the grip and should learn which to use for different tasks.

---

### Post by aysiu on 2006-09-07
Imagine there's a Chinese bakery that you visit in Chinatown. You don't speak any Chinese, and the people who work there don't speak any English.

Well, you visit a few times a year, so you're pretty satisfied to just gesture frantically at bakery items and hold up your fingers to indicate how many of each item you want to buy.

Now, imagine that you live in Hong Kong, and there's a Chinese bakery and a Chinese restaurant and a Chinese bus and a Chinese bank and a Chinese clothing store--you visit all these places regularly. Then you might want to consider learning the minimal Chinese it takes to communicate effectively what bakery items you want and want clothes you want and what bus stop you want to get off at.

Same thing with computers. Computers do not speak English. For tasks you don't do regularly (if you're "just visiting," so to speak), it makes sense to have a point-and-click, since it's primitive (like gesturing frantically in a Chinese bakery) and "universal." If you have tasks you do every day, several times a day (let's say... you use your computer for your job from 9 AM to 5 PM), then it may be worth learning the computer's language to communicate more efficiently.

While the Chinese bakery cashier can learn English just as easily as you can learn Chinese, the computer cannot learn English as easily as you can learn terminal commands. To get to the point where you can just type in regular English commands would require some extremely sophisticated programming. In other words, it's a lot easier for you to learn ```
wget -c -r -l 2 http://www.somesite.com
``` than it is for a computer to learn how to interpret ```
computer, please fetch me the website http://www.somesite.com two levels down and make sure you continue to fetch it later if it only partially downloads
```

---

### Post by BLTicklemonster on 2006-09-07
Two things: 

1. I'd rather type sudo than deal with what evil things could happen if anyone could take control of my machine.

and

B. I'd rather have a bottle in front of me than a frontal lobotomy.

and 

3. ... no wait, there's not a 3. Wish I'd said something about that bottle sooner...

---

### Post by aysiu on 2006-09-07
> **BLTicklemonster said:**
> 
B. I'd rather have a bottle in front of me than a frontal lobotomy.
 How profound, BLTicklemonster!

---

### Post by The_Apprentice on 2006-09-07
> **aysiu said:**
> I don't see why this has become a command-line v. GUI thing.

*sudo* is for the command-line.
*gksudo* and *kdesu* are for the GUI.

**There's absolutely no reason you have to log in as root**, either graphically or in the terminal. If you feel the need to make root changes graphically, create a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` or ```
kdesu konqueror
``` and you're set. No need to log in as root.


I totally agree that the CLI is extremely powerful.  I found DOS (and still do) far more powerful than the GUI to undertake a great number of tasks.

Personally I just need to re-learn much of what I already know about Windows/DOS for the Linux environment, and I am really enjoying doing that.

Why quote the post?
'Cos using "gksudo nautilus" is exactly what I want, and probably will be all I will ever want for quick and easy fixes to configuring my system directory structure how I want it.  I can even edit a configuration file should it take my fancy.

I now have the time to learn the technical basics of configuration and security, leading me to progess with Linux and be as good as I am with Microsoft based operating systems, which currently keeps me with a comfortable standard of living.

In time I hope to be able to offer a lot back to the community.

---

### Post by BLTicklemonster on 2006-09-07
> **aysiu said:**
> How profound, BLTicklemonster!

Hey, I remember you! :) So yeah, after being away for like 5 or 6 months, I can say that it was with much trepidation that I loaded up ubuntu, but things started coming back to me once I got in my groove. Heck, it was in no time flat that I messed up trying to add repositories, then after a reinstall, I hastily got some whack setuid error. 

Just kidding, I knew I'd still have problems. But using the command line was much easier and I remembered a lot of stuff. So it's not bad coming back and having to use the CLI after all. (but for everyday stuff, I'd as soon use my mouse)

---

### Post by Slaskpelle on 2006-09-08
" We were not talking about the look of course.
Do you think *power over computer* is linearly dependant from *colours on display*? "

Ah ok, sorry im a bit of a graphical kind of guy so i like my colours :rolleyes: 
When I was young i always thought people using *nix did so because they were colourblind, ah so wrong one can be! 

Anyway, I got some really good poweruser ideas for developing the Ubuntu kernel, where do I turn? I basically think I found a way to completely remove sudo with a kernel compile and a few tweaks! :)  


" Now I aint sayin she a gold digger But she aint messin wit no broke niggaz "

---

### Post by Lord Illidan on 2006-09-08
> **Slaskpelle said:**
> " We were not talking about the look of course.
Do you think *power over computer* is linearly dependant from *colours on display*? "

Ah ok, sorry im a bit of a graphical kind of guy so i like my colours :rolleyes: 
When I was young i always thought people using *nix did so because they were colourblind, ah so wrong one can be! 

Anyway, I got some really good poweruser ideas for developing the Ubuntu kernel, where do I turn? I basically think I found a way to completely remove sudo with a kernel compile and a few tweaks! :)  


" Now I aint sayin she a gold digger But she aint messin wit no broke niggaz "

What's it with you and sudo??](*,)

---

### Post by Slaskpelle on 2006-09-08
> **Lord Illidan said:**
> What's it with you and sudo??](*,)

Dear Lord,

My feelings for sudo are quite clear, it really is a N00biez lap dog in my well established opinion.

Once as root i typed:-

rm * / -fvr 

Can you guess what happened??....  absolutely nothing! Why u ask?

The answer is simple..

My system resisted the command! Unfortuanaly though, in the power struggle of good and evil "rm" corrupted badly. Ah well who needs it.

This will be addressed in my next "HOWTO" - "Making a beefcake out of your ubuntu in 3 weeks - guaranteed!"

:biggrin:

---

### Post by Lord Illidan on 2006-09-08
> **Slaskpelle said:**
> Dear Lord,

My feelings for sudo are quite clear, it really is a N00biez lap dog in my well established opinion.

Once as root i typed:-

rm * / -fvr 

Can you guess what happened??....  absolutely nothing! Why u ask?

The answer is simple..

My system resisted the command! Unfortuanaly though, in the power struggle of good and evil "rm" corrupted badly. Ah well who needs it.

This will be addressed in my next "HOWTO" - "Making a beefcake out of your ubuntu in 3 weeks - guaranteed!"

:biggrin:
Dear Slaskpelle...

3 weeks??
I could do it in 3 secs :) :) :) :)
be blessed!

---

### Post by Slaskpelle on 2006-09-08
> **Lord Illidan said:**
> Dear Slaskpelle...

3 weeks??
I could do it in 3 secs :) :) :) :)
be blessed!

Dear Lord. 

I am sure you could do that to some extent if you had a really beefy computer, but I am not talking about boosting your kernel by removing unwanted modules from /lib/modules using the "rm -fvr" command. Neither am i talking about making graphics faster by installing the "nvidia" driver for full colour card support. We have all seen these tweaks before Lord, no need to post them again. 

What my "HOWTO" is gonna be about is how to make "BEEFING" possible on a higher more "power user" plane, by removing code (the Sudo code amongst other snippets) from the actual Ubuntu source and recompiling from scratch using secret compilers. 


" No New Year's Day to celebrate
No chocolate covered candy hearts to give away
No first of spring
No song to sing
In fact here's just another ordinary day "

---

### Post by angkor on 2006-09-08
> **Slaskpelle said:**
> If you'd like to also become a "POWER USER" follow these simple, simple instructions.


*lol*

Slaskpelle, you are nowhere near the poweruser you claim to be, I have absolutely no problem with you explaining (in a rather strange way) how to enable a root account on Ubuntu. 

I do have a problem however that you're howto doesn't mention the dangers (security-wise) of graphically logging in as root. When you try to be helpful to new users you'll need to inform them of the pros, cons and dangers of what you propose in your howto.

---

### Post by Slaskpelle on 2006-09-08
My "HOWTO" isn't really intended for new users but rather for more advanced "POWER USERS" with full awarness of the security issues in ROOT/GUI Vs the simpleton terminal.

---

### Post by K.Mandla on 2006-09-08
What's funny to me is, when I use Arch, I start out like this. ...

```
passwd root
pacman -S sudo
adduser kmandla
nano /etc/sudoers
```
In other words, the first thing I do is set up a sudo account for myself. ...

After working for so long with Ubuntu, logging in and working as root is ... kinda creepy. :-|

---

### Post by angkor on 2006-09-08
> **Slaskpelle said:**
> My "HOWTO" isn't really intended for new users but rather for more advanced "POWER USERS" with full awarness of the security issues in ROOT/GUI Vs the simpleton terminal.


These so-called "more advanced power users" will have no use for your howto, because:

a) They already know howto enable and use a root account wisely
b) They already know that graphically logging in as root is about the       stupidest thing you can do to your linux box.
c) They are fully aware that logging in as root (graphically) is *never* necessary to perform systems tasks.
d) They aren't scared of the terminal and don't consider it outdated or "simpleton" or whatever notion *you* have of the terminal.

---

### Post by Slaskpelle on 2006-09-08
> **K.Mandla said:**
> What's funny to me is, when I use Arch, I start out like this. ...

```
passwd root
pacman -S sudo
adduser kmandla
nano /etc/sudoers
```
In other words, the first thing I do is set up a sudo account for myself. ...

After working for so long with Ubuntu, logging in and working as root is ... kinda creepy. :-|

Nothing wrong with living on the edge ever so often, gives your adrenaline a boost. Also, I found through experience that admins that always use their root account rather than sudo are generally more security aware and takes bigger precautions to avoid "hackers", for example by unplugging their T3 line when they're finished their online bussiness, or by shutting their servers down in the evening. 

My feelings for ubuntu as said by "cpl Lionel" -->

" Say you, say me; say it for always
Thats the way it should be
Say you, say me; say it together
Naturally "

---

### Post by whizbaby on 2006-09-08
> **Slaskpelle said:**
>  Also, I found through experience that admins that always use their root account rather than sudo are generally more security aware and takes bigger precautions to avoid "hackers", for example by unplugging their T3 line when they're finished their online bussiness, or by shutting their servers down in the evening. 

An admin shutting down the servers in the evening (I would get roasted for this)? Are you aware of what you're saying? Didn't know that the internet is turned off at night time...
(and PLEASE stop this root<->sudo talk and get to know how the system is supposed to be used instead of playing DJ CoolMcRoot)

---

### Post by Slaskpelle on 2006-09-08
Look people, If i cant get through to you in words... then, maybe a song?

Lets hope your crusty cli supports this! Oh, and make sure your speakers are loud and your alsamixer is redlining!!!!

LEMMI SEE YOU SAY YEAH!!!!


[http://www.youtube.com/watch?v=RIS8ImTPGvc](http://www.youtube.com/watch?v=RIS8ImTPGvc)

---

### Post by cstudent on 2006-09-08
I think Crazy Dave from American Idol has wandered into the forums.

---

### Post by blackened on 2006-09-09
Styrofoam-eating progeny of Vince Vaughn and Screech from Saved By The Bell unite!

This discussion has been reduced to bad 80s mullet-pimping song quotes, so I'm gonna break it down.

root = great for more advanced users who know its' proper place, but better to not post such things for absolute rookies.

sudo = god's gift to Lionel Richie and his fans.. and newbies too.

---

