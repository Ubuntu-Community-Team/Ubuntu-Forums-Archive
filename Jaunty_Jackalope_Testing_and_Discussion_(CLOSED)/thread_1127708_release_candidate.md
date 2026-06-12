---
title: "release candidate"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bert Mariën on 2009-04-16
Just installed the RC.

Many programs are still not to be found in the repositories.

KompoZer does not startup.
Root terminal does not startup.

Couldn't uninstall the GNOME games via Add/Remove (no games are displayed).

!!! But worst of all, when booting and trying to login, Jaunty does not use the correct keyboard for my system (be-latin1), so I have troubles login in because of my password. :(
!!! I hope the developers read this, because I DID install with the right (Belgian) keyboard !!!


Does anyone know a work-around, or knows how to solve this? (Booting with the correct keyboard BEFORE logging in.)

For the rest...
Good, very good work guys (and dolls).

---

### Post by Bert Mariën on 2009-04-16
Oh yes, notice the "bird" icons of Sunbird. (Thank you.)

Alas the install screen from of step 4 still does not fit the screen (for my system anyway). That is bug #272318.
It might have fit if I should use a "broad screen". Don't know. Can't test it.

---

### Post by llamakc on 2009-04-16
If you have a bug (concerning the keyboard settings) you need to search for and file a bug. Good luck.

---

### Post by andrewabc on 2009-04-16
> **Bert Mariën said:**
> Oh yes, notice the "bird" icons of Sunbird. (Thank you.)

Sunbird still doesn't work?
It never worked for me in intrepid. Sad to hear it still has problems.

---

### Post by Bert Mariën on 2009-04-16
Sunbird ALWAYS worked here.
Just wanted people to notice that the "bird icons" finally arrived in the Ubuntu distro.

---

### Post by Bert Mariën on 2009-04-16
I might have found the solution for the keyboard issue whilst installing the Xubuntu RC.

When installing you are provided with a "suggested" keyboard choice. Although it might even be the correct one, change it to your own choice, and select your keyboard.

It worked in Xubuntu.

I'm going to try it now again installing Ubuntu anew.

---

### Post by Kevrox on 2009-04-16
The Rc installed ok.
BUt a few thing still remain from last intrepid install.
I had to run sudo update-apt-xapian-index to get the SPM to do a search in the quick search option.
There is still the annoying PC beep at shut down, I stopped it with this sudo gedit /etc/modprobe.d/blacklist, then placed this &#8211; blacklist pcspkrat &#8211; at the bottom and saved and rebooted. Beep gone.

one other thing and yes I know it is filed in the intrepid section but how would I go about getting this done even a hack would be nice. 
I posted this bug a while ago and nothing happened. perhaps I did not follow protocol.
Bug #340442:
This report is public


Binary package hint: libgweather-common

I would like to have my town added to the locations selection for the Weather Report 2.24.1 applet
Location of local airport is as follows.
Country Australia
ICAO ID YBUN
Time UTC+8
Latitude -33.378333
33° 22' 42.00" S
Longitude 115.676667
115° 40' 36.00" E
I think this is all that I have seen requested for this to be done. Many Thanks in advance.
Kev

1) The release of Ubuntu you are using, --Ubuntu 8.10 (intrepid), 2.6.27-13-generic (#1 SMP Thu Feb 26 07:26:43 UTC 2009)
2) The version of the package you are using, --- Weather Report 2.24.1 applet (GWeather-common2.24.1)
3) What you expected to happen --- To see Bunbury Western Australia shown
4) What happened instead --- Perth location ( 200km north of Bunbury)

---

### Post by Bert Mariën on 2009-04-16
I was right abought the keyboard issue.

Instead of choosing the "suggested" keyboard, choose "choose your own" and than select the desired keyboard layout.

This solves the problem for non US keyboards.

This also means that the suggested keyboard (although correct) does NOT ACTIVATES the correct keyboard layout. 

devs??? Hear this?

---

### Post by Bert Mariën on 2009-04-16
> **Kevrox said:**
> 
There is still the annoying PC beep at shut down, I stopped it with this sudo gedit /etc/modprobe.d/blacklist, then placed this – blacklist pcspkrat – at the bottom and saved and rebooted. Beep gone.

Normally you can stop the beeps following these links:
System > Preferences > Sound > Sounds

 and than unmark:

- play alerts and sound effects;
- play alerts sounds

---

### Post by Bert Mariën on 2009-04-16
I don't like my system "beeping" and "ringing" either. First thingy I turn of is the sound. ;)

---

### Post by Bert Mariën on 2009-04-16
Especially on (very) noisy MS Windows!
;):P:)

---

### Post by Bert Mariën on 2009-04-17
> **Bert Mariën said:**
> Especially on (very) noisy MS Windows!
But that is besides the point and the issue here!
Sorry for that!

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Normally you can stop the beeps following these links:
System > Preferences > Sound > Sounds

 and than unmark:

- play alerts and sound effects;
- play alerts sounds

I tried that. sudo gedit /etc/modprobe.d/blacklist.conf  - blacklist pcspkr - seemed to be the only thing to work. BUT in Debian Lenny there is an extra tab in the System > Preferences > Sound next to the Sound Tab that allows one to turn off the pc speaker. It worked there but there is no third tab in Ubuntu. I had no beep sound with intrepid only Jaunty at the moment.

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> There is still the annoying PC beep at shut down
Okay. I noticed it as well.
Tried your solution, but it didn't work for me.
Unless I wrote it in the wrong file.

Can you please! tell me in exactly which file you wrote 
blacklist pcspkrat

and what it does mean (I am not THAT familiar concerning linux).

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Okay. I noticed it as well.
Tried your solution, but it didn't work for me.
Unless I wrote it in the wrong file.

Can you please! tell me in exactly which file you wrote 
blacklist pcspkrat

and what it does mean (I am not THAT familiar concerning linux).


open up a terminal and paste
sudo gedit /etc/modprobe.d/blacklist.conf
it will ask for your password, then it will open this file, next copy and paste 

# Remove Annoying beep on shutdown
blacklist pcspkr

and place at the end of all the other text save and quit and reboot.
From my understanding it stops any activity to and from the PC speaker. The advantage no annoying beet that scares the daylights out of me when I least expect it and the down side is you will not get error alerts . As i said I think that is how it works.

---

### Post by Bert Mariën on 2009-04-17
To Kevrox:

It works. 
But stopping all activity to the speaker, won't it stop you from playing music as well?

Thanks for the info and the solution!

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> To Kevrox:

It works. 
But stopping all activity to the speaker, won't it stop you from playing music as well?

Thanks for the info and the solution!

it only seems to apply to the PC speaker and not the sound system in the pc like the output to your speakers or ear phones. give it a try with mp3 music or music cd or utube video.

Your Welcome... I've been ubuntuing for just on a year now ... loving it

---

### Post by Bert Mariën on 2009-04-17
Nope. I heard it play.

So what does that "blacklist..." really do?

And I MUST say, I do not know what "blacklisting" really means.
Can you (or anyone else) enlighten me?

---

### Post by Bert Mariën on 2009-04-17
Yes, I know...
But I'm still learning, and eager to do so!

---

### Post by nystire on 2009-04-17
Blacklisting that particular driver simply means that Jaunty will not load it. It won't affect anything else (unless suddenly there are other programs/drivers which depend on the pc speaker working - hightly unlikely).

---

### Post by Kevrox on 2009-04-17
I remember finding this info here
[http://www.howtogeek.com/howto/ubuntu/disable-the-system-beep-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/disable-the-system-beep-on-ubuntu-edgy/)

Google a bit or look in the ubuntu help section should tell us something more.:D

That 3rd tab is what I was talking about, does anyone know where we can enable it.

---

### Post by Bert Mariën on 2009-04-17
So "pcspkr" is a driver.

I surely didn't know that. Couldn't know that by it's name alone.

Thanks very much for the info.

---

### Post by Kevrox on 2009-04-17
> **nystire said:**
> Blacklisting that particular driver simply means that Jaunty will not load it. It won't affect anything else (unless suddenly there are other programs/drivers which depend on the pc speaker working - hightly unlikely).

thanks for that

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> I remember finding this info...
That 3rd tab is what I was talking about, does anyone know where we can enable it.

Didn't you find the (more or less) same thing following the >>>>> as I wrote before?

---

### Post by Bert Mariën on 2009-04-17
;)
We are "nice" to each other today, aren't we?
:D

---

### Post by Bert Mariën on 2009-04-17
But I must say:
There aren't many reactions on the RC coming in....

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Didn't you find the (more or less) same thing following the >>>>> as I wrote before?

Do you mean the tab that says "system beep"

On my system here I do not have that tab option at all.

---

### Post by Bert Mariën on 2009-04-17
No, I mean:

Following these links:
System > Preferences > Sound > Sounds

and than unmark:

- play alerts and sound effects;
- play alerts sounds

---

### Post by Bert Mariën on 2009-04-17
You are in Jaunty now, aren't you?

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> No, I mean:

Following these links:
System > Preferences > Sound > Sounds

and than unmark:

- play alerts and sound effects;
- play alerts sounds

I found those ok and disabled them but still had the system beep on shutdown. Hence the blacklist option.:D

---

### Post by Bert Mariën on 2009-04-17
Unmarking those, should keep your system from "beeping".

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> You are in Jaunty now, aren't you?

YES the RC I downloaded last night from .pool and did a fresh install.

---

### Post by Bert Mariën on 2009-04-17
Your "blacklisting" thing does the rest...

Does it not for you?
It does here.

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Unmarking those, should keep your system from "beeping".

Perhaps it's a dell thing, my play toy is an old inspiron 630m

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Your "blacklisting" thing does the rest...

Does it not for you?
It does here.

Yes the blacklist thing was the only way to disable the beep on shutdown. BUT when i was stuffing about with Lenny the 3rd tab was an option and that worked.
In JAUNTY blacklist is the only thing that worked even with the sound options off.

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> YES the RC I downloaded last night...
So did I. :D
if you read the thread, you saw I had some issues with the keyboard. Which is solved now. Wel... solved in the meaning one can correct a problem just by interacting, and by not using the suggested keyboard....

But Jaunty looks good to me.
Still (too) many bugs for a RC though.

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> Perhaps it's a dell thing, my play toy is an old inspiron 630m

As you might have noticed: I'm on an Inspiron 531 here, and I also have an Inspiron 2200 upstairs, but I haven't tried the RC there yet....

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> So did I. :D
if you read the thread, you saw I had some issues with the keyboard. Which is solved now. Wel... solved in the meaning one can correct a problem just by interacting, and by not using the suggested keyboard....

But Jaunty looks good to me.
Still (too) many bugs for a RC though.


yip. was hoping the rc was the final without a few tweaks but perhaps by the 24 or 25 it may have a new iso in the download  mirrors. Will keep an eye for it in the.pools;)

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> As you might have noticed: I'm on an Inspiron 531 here, and I also have an Inspiron 2200 upstairs, but I haven't tried the RC there yet....

My thing is minus a battery and screen, ( plugged into a separate LCD )
Running on mains only, but hay a freebe is a freebe.

---

### Post by Bert Mariën on 2009-04-17
Oh no, you couldn't have noticed. 
That info is missing in my signiture.

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> yip. was hoping the rc was the final without a few tweaks...
If the community reports enough bugs and/or issues, the dev's will get it right before next week (release date).

---

### Post by nystire on 2009-04-17
> **Bert Mariën said:**
> ;)
We are "nice" to each other today, aren't we?
:D

Now is when we start to see how we all work under pressure to get everything fixed by release time :)

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> ...Running on mains only, but hay a freebe is a freebe.
That alone is a reason to change to a (any) linux distro. When you are short on cash anyway.

---

### Post by Bert Mariën on 2009-04-17
> **nystire said:**
> Now is when we start to see how we all work under pressure to get everything fixed by release time :)
I have more than big (great) respect for all the devs!

I will (shall) take my hat off.

---

### Post by Bert Mariën on 2009-04-17
> **nystire said:**
> Now is when we start to see how we all work under pressure to get everything fixed by release time :)
I try almost every Linux distro that sees the light of day; might be up to 10 distros a week.

I must say:
the GNOME version of Ubuntu is far out the best, easiest and fasted to update, easiest to install programs and so on....
And... not to forget...:
I believe that the Ubuntu community is far out the biggest and most active community Linux has ever seen.

:D
Praise the Lord. ;)

---

### Post by Bert Mariën on 2009-04-17
Just to acknowledge this:
at the moment that I write this, there are 7288 members on the forum!!!!

---

### Post by Bert Mariën on 2009-04-17
And that is only the "official" forum. Not to mention the forums in other languages!!!!

---

### Post by nystire on 2009-04-17
And most of them are frantically searching for a fix of some sort? :D

---

### Post by Bert Mariën on 2009-04-17
> **nystire said:**
> And most of them are frantically searching for a fix of some sort? :D
Yes, but that's what keeps the community alive.
And... bound to be together.

New friends...

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Unmarking those, should keep your system from "beeping".

OK had a bit of a play reboot and play again.
Conclusion.
The unmarking of 

- play alerts sounds

That works for console errors and the like. So the on off option works ok for that. BUT the beep when shutting down must come from the Fast User Switch Applet 2.24.0 error ( 2.24.0.Oubuntu13) . Intrepid does not do this and shutting down with the drop down menu method also creates the beep in intrepid but using intrepid Fast User Switch Applet it does not.... mmmmmmm something has changed with the  Fast User Switch Applet then.

---

### Post by Bert Mariën on 2009-04-17
At least, unlike some other individuals, we help, or try to help each other.

What can be more beautiful in life?

Except love of course...:D;)

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> ...must come from the Fast User Switch Applet 2.24.0 error. Intrepid does not...
Indeed, Intrepid did not have this issue.
But what is:
Fast User Switch Applet?

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Indeed, Intrepid did not have this issue.
But what is:
Fast User Switch Applet?

top right hand corner of screen, your log in name and red shutdown button, Right click over the icon and hit about or help.

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> top right hand corner...
Okay,I got it.
I had it since Intrepid anyway.:guitar:
Just... I didn't realize for a moment what you meant.
Sorry.:guitar::P

---

### Post by Bert Mariën on 2009-04-17
I also did some fiddling.
Removed the "blacklisting", rebooted, rebooted again but not using the FUSA?

Still beeped. So is is not the Fast User Switcher Applet that causes this?

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> I also did some fiddling.
Removed the "blacklisting", rebooted, rebooted again but not using the FUSA?

Still beeped. So is is not the Fast User Switcher Applet that causes this?

Bummer. Back to Black list then:D

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> Bummer. Back to Black list then:D
Sigh.

---

### Post by Bert Mariën on 2009-04-17
I also noticed that this thread has been read about a 700 times, but somehow people do not seem to have any problems with the RC because no new posts come in at this thread.????

I think they should post if they "got" something that could help the devs.

Or maybe most of them think there is nothing wrong with the RC.
It's a possibility....

---

### Post by Bert Mariën on 2009-04-17
Surely cannot be that the "beep" thing is the only thing wrong with the RC.
I have knowledge of at least 2 more things crashing...

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> I also did some fiddling.
Removed the "blacklisting", rebooted, rebooted again but not using the FUSA?

Still beeped. So is is not the Fast User Switcher Applet that causes this?

Ok it must be the Fast User Switch Applet 2.24.0 (2.24.0.Oubuntu13)

I just removed the ( 2.24.0.Oubuntu13) and replaced it with the ( 2.24.0.Oubuntu6) from intrepid and removes the blacklist speaker line and rebooted , NO SHUTDOWN NOISE!! YAHOOOO

fast-user-switch-applet_2.24.0-0ubuntu6_i386.deb

My day is done. cheers till tomorrow.

---

### Post by Kevrox on 2009-04-17
> **Kevrox said:**
> Ok it must be the Fast User Switch Applet 2.24.0 (2.24.0.Oubuntu13)

I just removed the ( 2.24.0.Oubuntu13) and replaced it with the ( 2.24.0.Oubuntu6) from intrepid and removes the blacklist speaker line and rebooted , NO SHUTDOWN NOISE!! YAHOOOO

fast-user-switch-applet_2.24.0-0ubuntu6_i386.deb

My day is done. cheers till tomorrow.


There is no count down but hay I do not care it's quiet.

---

### Post by Bert Mariën on 2009-04-17
Seeing you tested it all.
You must be right, and it is the FUSA.
Did you file a bug?

---

### Post by Bert Mariën on 2009-04-17
> **Kevrox said:**
> Ok it must be the Fast User Switch Applet 2.24.0
:guitar:
And so you were right from the beginning!
Smart, that is!
:guitar:

---

### Post by Bert Mariën on 2009-04-17
Aye people, this thread is meant to be used by people that have troubles/experians with the CR release.
Let it all "flow" out.

---

### Post by Kevrox on 2009-04-17
> **Bert Mariën said:**
> Aye people, this thread is meant to be used by people that have troubles/experians with the CR release.
Let it all "flow" out.

More flowing.... I have tracked down the fast-user-switch-applet_2.24.0 that changed from quiet to annoying.. it was 
fast-user-switch-applet_2.24.0-0ubuntu8_i386.deb,


fast-user-switch-applet_2.24.0-0ubuntu6_i386.deb worked well
fast-user-switch-applet_2.24.0-0ubuntu7_i386.deb had a slight glitch on first load up but was fine after that.


fast-user-switch-applet_2.24.0-0ubuntu8_i386.deb - annoying
fast-user-switch-applet_2.24.0-0ubuntu9_i386.deb - annoying
fast-user-switch-applet_2.24.0-0ubuntu10_i386.deb - annoying
fast-user-switch-applet_2.24.0-0ubuntu13_i386.deb latest release - annoying

all have the annoying beep even after you let the 60 seconds go by.

---

### Post by deanjm1963 on 2009-04-17
As far as kompozer goes, it doesn't work in jaunty. It's not a "jaunty problem", it has to do with the version of gecko it's written with, it's not compatible with the latest gtk - all new distros (alphas, betas) e.g. ubuntu, fedora, are having problems with it.

The work around is simple.

go to [http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2]("http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2") and download the linux archive. uncompress it and open nautilus as root (alt-f2 gksudo nautlius) and copy the extracted folder to /opt ... then make a menu entry with "Main Menu).

Works very well for an alpha, no crashes for me so far. Hope this helps.

---

### Post by cl333r on 2009-04-17
I haven't read all pages, but in reply to your first post:
```

sudo aptitude remove --purge gnome-games gnome-games-data

```

--purge is in case you also want to remove the cache of the games so disk space is actually freed.

---

### Post by alphacrucis2 on 2009-04-17
> **deanjm1963 said:**
> As far as kompozer goes, it doesn't work in jaunty. It's not a "jaunty problem", it has to do with the version of gecko it's written with, it's not compatible with the latest gtk - all new distros (alphas, betas) e.g. ubuntu, fedora, are having problems with it.

The work around is simple.

go to [http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2]("http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2") and download the linux archive. uncompress it and open nautilus as root (alt-f2 gksudo nautlius) and copy the extracted folder to /opt ... then make a menu entry with "Main Menu).

Works very well for an alpha, no crashes for me so far. Hope this helps.

Three cheers for Kazé. He is putting a lot of work into this. 0.8 isn't just a fix either. The new DOM bar is cool. The new source dock took me a bit of getting used to but it is getting there.

---

### Post by Bert Mariën on 2009-04-17
> **cl333r said:**
> I haven't read all pages, but in reply to your first pos...
It was possible do do so using Synaptic....
But thanks!

---

### Post by Bert Mariën on 2009-04-17
> **alphacrucis2 said:**
> Three cheers for Kazé...
And for all the other Ubuntu developers, I asume.
They earned it. They deserve it.

---

### Post by lisati on 2009-04-17
Downloaded & burned the Release Candidate. The LiveCD boots & gets to the desktop, but XP seems to be having trouble with the disk's autoplay.... sigh, will have to troubleshoot and see if it's a bad burn or what.... I wonder if Wubi will work if I access the disk via "explore".....

(wanders off to investigate)

EDIT: (wanders back) Could just be XP packing a mental, the "Check CD for defects" option reported "no errors". CD boots OK & the "Try Ubuntu" option seems to work OK - nice splash screen modifications.

---

### Post by Bert Mariën on 2009-04-18
> **lisati said:**
> The LiveCD boots & gets to the desktop, but XP seems to be having trouble with the disk's autoplay.... 
I must say, it didn't acure to me to test installation on a Windows partition.
But thanks for bringing this up. I might just try it myself.

---

### Post by Kevrox on 2009-04-18
> **Kevrox said:**
> More flowing.... I have tracked down the fast-user-switch-applet_2.24.0 that changed from quiet to annoying.. it was 
fast-user-switch-applet_2.24.0-0ubuntu8_i386.deb,


fast-user-switch-applet_2.24.0-0ubuntu6_i386.deb worked well
fast-user-switch-applet_2.24.0-0ubuntu7_i386.deb had a slight glitch on first load up but was fine after that.


fast-user-switch-applet_2.24.0-0ubuntu8_i386.deb - annoying
fast-user-switch-applet_2.24.0-0ubuntu9_i386.deb - annoying
fast-user-switch-applet_2.24.0-0ubuntu10_i386.deb - annoying
fast-user-switch-applet_2.24.0-0ubuntu13_i386.deb latest release - annoying

all have the annoying beep even after you let the 60 seconds go by.

Bug Filed Bug #363321:
[https://bugs.edge.launchpad.net/ubuntu/+bug/363321](https://bugs.edge.launchpad.net/ubuntu/+bug/363321)

---

### Post by Bert Mariën on 2009-04-18
> **Kevrox said:**
> Bug Filed Bug #363321:
[https://bugs.edge.launchpad.net/ubuntu/+bug/363321](https://bugs.edge.launchpad.net/ubuntu/+bug/363321)
This is why beta (and other) testers are so important to the community.

---

### Post by tazd on 2009-04-18
Well i must say the only thing i am having problems with is my Atheros 5007EG wireless card. It worked fine in the beta untill i upgraded to the RC and now the system doesn't even see it. Just need to try and figure out how thw the heck to get this system to see the card again.

Apart from that i am very happy with the RC

---

