---
title: "[SOLVED] Installing EXE Files Help? Yeah, I'm New."
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Dunpiel on 2008-03-05
Forgive me for being new here but not being new to computers but being NEW NEW to Ubuntu/Linux.

I've known about Linux, Red Hat, Ubuntu for sometime now but have only recently been forced to
this alternative because of a trojan that forced my g/f's laptop (that I'm typing on) to go into some
stupid *** loop of restarts stating: "disc read error...press CTRL+ALT+DEL to restart" Ugh.

I've no backup XP discs, boot discs, ect so I'm resorting to Ubuntu, but I'm pissed because I'm short
on patience and tall on seriously wanting to learn Ubuntu as it's always told to be 'user friendly'
although when I first interfaced with it and tried installing an .exe file (Zoom Player), it most 
definitely seemed the opposite.

I went to the Beginner's Forum, got a feel for the SUDO, but installing Win executables still doesn't
make sense to me through Ubuntu with all this text-based commands to be done...

TRUST me when I say to you---when something presents itself to me as difficult, I usually get
really pissed (as with some of my favorite insane difficulty videogames) but then I'm like: "****
this...I'm mastering this baby." 

*edit* I know about Wine but that makes things even less 'user friendly' to me...but of course
I'm here on this forum hoping that ONE of you could atleast show me the way...

So thanks for listening/your time, I just would like to get started with the .exe installs if I could.

---

### Post by wieman01 on 2008-03-05
You cannot install Windows .EXE files on a Linux machine, unless you use Wine of course. Before we go into the details, what program do you want to install and would you also accept an OS Linux alternative? You know, there are tons of Linux programs & applications out there, so perhaps you don't need the Windows one after all. 

What is it you are trying to install?

---

### Post by jrusso2 on 2008-03-05
His post indicates he was trying to install Zoom player.  There are many native linux media players such as Mplayer, Kaffeine, Xine, Totem and kmplayer which are in the repository for you to try.

---

### Post by wieman01 on 2008-03-05
Ah, you beat me to it, jrusso2.  Thank you.

Yes, I agree with jrusso2, the options listed are a good start. Let me also mention **VLC** while we are at it. There is no need to actually install Zoom Player at all.

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]Okay. I actually know about VLC but not sure if I've ever used it. That one is also Win-compatible
is it not? 

Thankyou for giving me the alternatives you guys because I honestly do not know what they are
as you may have guessed---from not even knowing Ubuntu from my own butt. Tah.

On a side note my query was to also find out what all .exe files I could use on Ubuntu, because well,
like I saw in someone's signature:"Hi, my name is so-n-so, and I am a recovering Windows user."
Argh.

I most definitely am always interested in alternatives to the norm because that is how I found
Zoom Player in the first place to try something new outside of the WinConglomerate....so I'm gonna
give these suggestions a whirl.

Side note: I really do like WinAmp though....[/COLOR]

---

### Post by wieman01 on 2008-03-05
If you like Winamp, then you will also like XMMS which is fairly similar. 

VLC runs both on Windows & Linux if that's what you mean. On a side note, avoid Windows programs on Linux, it's a waste of time in 95% of the cases. There are exceptions though... But Zoom Player isn't one of them.

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]Hmm I just tried to install Aptitude (it was recommended when I went to d/l XMMX) and it's giving
me error: Dependency is not satisfiable: libapt-pkg-libc6.6-6-4.5

What now?[/COLOR]

---

### Post by wieman01 on 2008-03-05
There is a package manager called Synaptic. Please open it, enter your password and search for the relevant package. That's the easiest way.

---

### Post by hyper_ch on 2008-03-05
it will even sort stuff by category.

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]Okay I found Synaptic and opened it and upon opening it I read:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/COLOR]

---

### Post by RJ Hythloday on 2008-03-05
[quote=dibl]
Close anything resembling Adept or Synaptic, open the Konsole (Terminal-Bash) and enter ```
sudo dpkg --configure -a
```
If it does not give errors, then continue with ```
sudo apt-get update
```
```
sudo apt-get install
```
```
sudo apt-get autoclean
```
and you should be back in business. :)
[/quote]
 
these intstructions are for kubuntu but I think they'll be the same in gnome.

---

### Post by hyper_ch on 2008-03-05
RJ:

Is in those commands anything KDE specific invoved? --> nope --> so it works on all *buntu.

However
```

sudo apt-get install

```
should produce an error as you did not give any packages that shall be installed.

---

### Post by RJ Hythloday on 2008-03-05
all 4 codes, done 1 at a time, clears a known problem w/ adept, it sounds the same as the problem he's having w/ synaptic.

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]What's the deal? Does Ubuntu not want me to listen to my MP3s or what?

The first one I d/led said that the packet was broken (XMMS) and so now I tried a different d/l mirror
and now the error reads: Dependency is not satisfiable:libasound2[/COLOR]

---

### Post by hyper_ch on 2008-03-05
what download mirrors are you trying to use? Just use apt-get, aptitude, synaptic or adept.

---

### Post by iSplicer on 2008-03-05
Thats the beauty of Linux. It works in a completely different way to windows. What makes it even more awesome Is that there are extremely good alternatives to 99% of Windows software.

Cheers, and you can install VLC completely by typing in the terminal:

```
sudo apt-get install vlc
```

---

### Post by Dunpiel on 2008-03-05
[COLOR="Purple"]All I want is XMMS currently. All the mirrors from Ubuntu's own site is giving me faulty packages
apparently...*sigh* If Ubuntu/Linux is going to be this much trouble daily...LOL, forget it.[/COLOR]

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]Okay I don't know what happened but I still cannot d/l any XMMS that works/will install.

Also suddenly I can't download stuff to my desktop like I was just a few minutes ago...WTH happened?[/COLOR]

---

### Post by hyper_ch on 2008-03-05
did you notice that you do not give any details at all... all you say "this does not work"... you don't give any description of what you do and how you do it... neither of any error messages that occur... you neither state whether suggestions made here helped at all...

that makes is really hard to help you.

---

### Post by tact on 2008-03-05
You are going to "download sites" for software?    Thats windows behaviour...   not needed with Linux in like 99% of cases.  Learn another way....a much better way...

So much of the software you may want is already stored in "repositories".   You find them by either:
1.  using the synaptic package manager or...
2.  click on "Applications" and then "Add/Remove ..."
(there is a "command line" way to do it if you already know the package name and as others have already pointed you to).

Now I understand you may have broken the mechanism underneath "Synaptic" and the "Add/Remove"  functions.  You got an error message like ""E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

To "manually run" that command you need to open a terminal (command line) window and type it in exactly as it says ....
```
dpkg --configure -a
```

Others have given this advice but I see as has hyper_ch that you don't give any response whether you tried the advice and what was the result.  This does make it very hard to help you.

No Linux is not this hard to live with daily...  You managed to break something and people want to help you fix it.  Help people to help you.  Once the synaptic problem is fixed (and its very easy to do so) ...  then you will have no problems downloading and installing any of the 23,000+ software packages waiting for you.

The REAL "problem" is having SO MANY choices of software to try out and enjoy even for just one job - like listening to MP3.

You realise you don't have to download anything to play MP3s?   If you are using ubuntu then rhythmbox is installed by default (Applications>Sound and Video>Rhythmbox).   If you are on kubuntu there is another package installed already by default...etc.  

Look and Learn.

---

### Post by wieman01 on 2008-03-05
> libasound2
There is a package missing, please install it along with XMMS. It's in the repositories (i.e. Synaptics) as well. If you encouter such problems in future, simply install the relevant packages.

What's the status right now?

---

### Post by wieman01 on 2008-03-05
If you are comfortable with command line (terminal) then you could also issue the following command:
> sudo apt-get install libasound2 xmms 
Enter your password when prompted.

---

### Post by hyper_ch on 2008-03-05
> **tact said:**
> To "manually run" that command you need to open a terminal (command line) window and type it in exactly as it says ....
```
dpkg --configure -a
```

Just the "sudo" needs to be added at the front... otherwise it won't work.

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]Okay, (next afternoon, after staying up til 5AM reading stuff) I'm starting to understand why the
Terminal is faster than the normal find program page d/l site, d/l, install with Windows, is faster,
since it pretty much just does all that without you even leaving the Terminal. Nice.

I did the:

sudo apt-get install libasound2 xmms

and it worked fine. HOWEVER when again I d/led XMMX from a mirror  on Ubuntu's own links, it again
gave me the same error: Dependency not satisfiable:libasound2. I'll go back to the second page
to see if I missed anything. I'm still trying guys....[/COLOR]

---

### Post by Dunpiel on 2008-03-05
[color=indigo]Plus I get this from the Add/Remove-Apply options:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I HAVE run the steps it says to do but it keeps putting me back in this loop of
the same stuff over n' over. [/color]

---

### Post by SunnyRabbiera on 2008-03-05
looks like you are getting hiccups.
No worries, try a different app.
audacious is another winamp like program for linux.
also if you need some extra media stuff it might not be enabled by default.
No worries here either, in synaptic there is a way to edit the repositories.
when you go into synaptic go to "settings" and then to "repositiories"
here is where you can add extra repositories, enable all of them except for the last one and in the next tab over put a little check in the partner repositories.
more then likely you dont have the repos you need, thus why you are having problems

---

### Post by Dunpiel on 2008-03-05
[color=indigo]I'm not going to try anything else. I've not been able to install ANYTHING successfully. They've all
given me errors, so I'm sticking with just trying to get XMMS to work. [/color]

---

### Post by Kerin on 2008-03-05
I'm a little concerned your system may have hardware issues, especially considering how Windows imploded on you.  Try running memtest86 from the bootloader.

---

### Post by Dunpiel on 2008-03-05
[COLOR="Indigo"]Exactly how do I do that?
[/COLOR]

---

### Post by wieman01 on 2008-03-05
There is a memory test that you can select from GRUB. It is installed by default. Do you get the option when you boot your PC?

This is really odd. Please also post:
> sudo cat /etc/grub/menu.lst

---

### Post by Dunpiel on 2008-03-06
[COLOR="Indigo"]I went to a chat site that didn't have ANYTHING to do with Linux/Ubuntu, found someone who knew Ubuntu
and told me that this whole time, ALL I need to type in the Terminal was:

sudo -i

...which logged me in as root, which in turn let me install XMMS without any problems whatsoever becuase
everything that I have been going through was all 'permission' based. HOW STUPID. In understand the
security feature and it's purposes but for installs that pose no threat to the machine or users, what a serious
waste of time! Wow.

SideNote: Weiman01 I tried that memory test as you instructed but the Terminal just turned and told me
'No such file or directory'[/COLOR]

---

### Post by wieman01 on 2008-03-06
Dunpiel, 

Did you not add the 'sudo' prefix? It's definitely a permission problem, but all instructions included it. How weird is that?

So XMMS is installed now? How do you like it?

---

### Post by deepclutch on 2008-03-06
exe on Linux-may be we should let him know (dont loose ur patience!):
[_**[COLOR=Blue]Linux is NOT Windows![/COLOR]**_]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by wieman01 on 2008-03-06
> **deepclutch said:**
> exe on Linux-may be we should let him know (dont loose ur patience!):
[_**[COLOR=Blue]Linux is NOT Windows![/COLOR]**_]("http://linux.oneandoneis2.org/LNW.htm")
I guess he knows. Been through it.

---

### Post by Kerin on 2008-03-06
> **Dunpiel said:**
> [COLOR="Indigo"]I went to a chat site that didn't have ANYTHING to do with Linux/Ubuntu, found someone who knew Ubuntu
and told me that this whole time, ALL I need to type in the Terminal was:

sudo -i

...which logged me in as root, which in turn let me install XMMS without any problems whatsoever becuase
everything that I have been going through was all 'permission' based. HOW STUPID. In understand the
security feature and it's purposes but for installs that pose no threat to the machine or users, what a serious
waste of time! Wow.

SideNote: Weiman01 I tried that memory test as you instructed but the Terminal just turned and told me
'No such file or directory'[/COLOR]


No need to get angry, chief.  Remember that your computer has no ability to know if something is harmful or not - your command could just as easily be to install a program that would destroy your filesystem or upload your personal information to scammers.  It requires permissions specifically so users unqualified to make the judgment of whether a package is safe or not are unable to muck things up too bad.

It sounds to me like you're having a lot of odd problems - some I sort of suspect may be user error - try to follow instructions to the letter, if you skip steps or miss details things tend not to work at all.  

You don't get to memtest from the console!  You access it when you first boot your computer and it asks which operating system to load (E.G. Ubuntu ******* on two lines, one being the recovery option) you press the Down key several times to select memtest86 instead of your operating system and then press Enter.

---

### Post by Dunpiel on 2008-03-06
> **wieman01 said:**
> Dunpiel, 

Did you not add the 'sudo' prefix? It's definitely a permission problem, but all instructions included it. How weird is that?

So XMMS is installed now? How do you like it?

[COLOR="Indigo"]Wieman I am trying the memory test again. I thought it was from Terminal. No
wonder the computer gave me blankness back. 

XMMS is nice. It IS just like WinAmp, menus n' everything. Which is nice. I don't mind alternatives
but there are just certain things that I like---the way they are. XMMS suits me so I'm stickin with it.
Plus, at the moment, I don't have to worry about any other music compression formats (ogg, ect)



[/COLOR]

---

### Post by wieman01 on 2008-03-06
Cool, it's settled then. Please mark this thread as "resolved" (Thread Tools" then. Let us know if you need more help and other little programs. Ubuntu is quite a pandora's box in a good sense.

---

### Post by snowdark on 2008-03-06
Hi! I'm a newbie. I think we can install file exten .EXE by software WINE. It looks like Mini Windows in Ubuntu and another Linux kernel. :KS

---

