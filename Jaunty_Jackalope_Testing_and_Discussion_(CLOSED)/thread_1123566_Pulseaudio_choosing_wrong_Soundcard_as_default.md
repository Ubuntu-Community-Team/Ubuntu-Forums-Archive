---
title: "Pulseaudio choosing wrong Soundcard as default"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dandandan on 2009-04-12
Hello fellow Ubuntu users

After upgrading to 9.04, pulseaudio chose the other Soundcard in my System to play the sound through.
My configurationlooks like that:

dan@sued0r:~$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf3ff8000 irq 22
 1 [Live           ]: EMU10K1 - SBLive! Value [CT4832]
                      SBLive! Value [CT4832] (rev.7, serial:0x80271102) at 0xe880, irq 17


in 8.10 pulse played through card 0, which is wanted behaviour.
in 9.04 pulse for some reasons plays through card 1 which is *not* wanted.
I put the sb live on slot 1 and not 0 for a reason.
I filled a bug report on launchpad, still can anyone tell me where i can tell pulseaudio to choose card 0 please, i really would like to watch videos with sound again :)

Thanks for your help

-dan

---

### Post by rbmorse on 2009-04-12
This post

[http://ubuntuforums.org/showthread.php?t=1122240&highlight=Bose+companion](http://ubuntuforums.org/showthread.php?t=1122240&highlight=Bose+companion)

is really directed at the Bose Companion V USB speaker system, but he talks about some tools that might help you address your issue.

---

### Post by dandandan on 2009-04-12
Big thanks rbmorse, now i can use pulse again.

This way shows the Problem even better, setting the default soundcard does not do *anything* in pulse, thats something the devs have to take a look at. Its annoying. Why pulse chooses not the default alsa card as its default is honestly beyond my comprehension.

---

### Post by markbuntu on 2009-04-13
Actually, in jaunty it is the other way around, alsa defaults to pulseaudio and lets pulse handle the hardware. Alsa default sound card setting should be deprecated since if you set that to a hardware device any alsa app can grab the device for exclusive use and other apps will not be able to use it. By having pulse as the default alsa device, pulse controls the hardware and applications can share.

---

### Post by dandandan on 2009-04-13
You are missing the point.
Ubuntu 8.10 -> sound
Ubuntu 9.04 -> no sound (well there is sound, but through the wrong soundcard which basically means no sound)

But i manually fixed that Problem now.

---

### Post by psyke83 on 2009-04-13
> **dandandan said:**
> You are missing the point.
Ubuntu 8.10 -> sound
Ubuntu 9.04 -> no sound (well there is sound, but through the wrong soundcard which basically means no sound)

But i manually fixed that Problem now.

The reason: Intrepid didn't configure PulseAudio to work by default in all cases, but Jaunty does. 

In Intrepid (and Hardy), most applications bypassed PulseAudio entirely unless you manually configured the PulseAudio ALSA plugins.

Your issue may have existed in Intrepid if PulseAudio was configured properly, so it's not really a new "bug".

Nevertheless, you can select the default sound card via the PulseAudio Volume Control applet (not installed by default, unfortunately).

From the [PulseAudio Fixes HOWTO]("http://ubuntuforums.org/showthread.php?t=789578"):

> Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

---

### Post by dandandan on 2009-04-13
Well that method does not work if you already tried to play sound.
You have to enter pacmd and unload the module which remember the stuff, del ya pulse files, restart session, choose default card, then you are good.
Or move every soundsource to the appropriate sink manually.

Anyhow, this is something the Ubuntu pulse guys should take a look at, since it breaks the Desktop.

---

### Post by markbuntu on 2009-04-14
The way pulse works is it remembers the device and volume of each application at its last use and restores that when the application is started which is quite reasonable behavior for the great majority of users. If you want the application to use another device just move the stream next time you play it and pulse will remember. 

Is that really so much harder than removing modules and deleting files and restarting your session etc?

Here are just a few examples of the problems encountered trying to decide how to do what you want. It is not so easy as you think.

Like should skype default to the bluetooth headset or the usb headest? Should it switch when bluetooth connection is lost? How is the fallback path determined? Should rythmbox move to the usb speakers when they are plugged in? What if it is broadcasting through an rtp sink or using SPDIF? How do you set a priority list for that? What should the gui look like? If it is too simple people will not have control they want, if it is too complicated people will be overwhelmed with too much information.

Anyway, there is an ongoing discussion about how to deal with the issue of what plays where and how to configure that and what a gui should do with multiple application defaults to multiple devices at the pulse mailing list. I suspect something will come out of it eventually. If you want an idea of where this is all going, look at the phonon sound configuration tool in KDE4.

Personally,I do not want all my sound apps moved automatically when I plug something new in. I prefer to be the one in control of my machine.

---

### Post by dandandan on 2009-04-14
Its is not harder, its is incomplete, if you dont remember every app you started.

Anyhow the Main Problem is, that PA worked great in 8.10 and did not work (straightly from a users point of view) in 9.04
I know how PA works, aftear reading up on my Problem, thats not the Point tho.
The Point is that after upgrading to 9.04 and you have 2 Soundcards your Desktop may be broken (meaning no sound anymore out of the Speakers), depending on which soundcard PA chooses as default.

I am not speaking of something hotplugable, no idea how you got to that idea :)

Dont get me wrong here, i appreciate the help and the ideas, still, from a users point of few -> 8.10 sound good -> 9.04 -> no sound
Thats all i am saying.

---

### Post by markbuntu on 2009-04-14
Well, I have 2 sound cards and a whole bunch of other sound stuff and nothing was broken, it just needed to be configured by me, the user. There is a big difference between broken and not user configured. And really, more than one sound card is a special case so it is up to the user to get it working. If I have no sound then the first thing I check is if the app is using the proper sink because I have two sound cards and a usb headset and a bluetooth headset and rtp sender and I can't remember where I sent the sound last time...and I need to set it up all over again when I do a new install, I have 6 different distributions running on this machine and besides Mandriva, Jaunty has been the easiest to set up.

In Hardy and Intrepid the sound WAS broken. Applications would not share the sound hardware, the pulseaudio guis were entirely missing along with other apps necessary to configure the sound.

If the sound worked properly in Intrepid I would not have had to write this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Much of which is irrelevant for Jaunty.

---

### Post by dandandan on 2009-04-14
*Sigh*

The Problem with it is, that PA configures it FOR you, in your case right, in my case wrong.
The is no popup asking me which soundcard i want to use, it just uses one, and remembers.
Assume one user has 2 Soundcards

Typically upgrade behaviour.

8.10 sound works great
upgrade to 9.04, PA chooses soundcard wrong (as in my case)
User wants to play Sound, non working, user tries ff youtube for example, not working, try a video, not working.

Most users dont have a CLUE whatsoever beyond here, since pa does not integrate in gnome control panel.

Lets assume an advanced user:
uses pavucontrol and sets default soundcard to the other.
tries to listen to music -> no sound, tries to watch a video -> no sound
Maybe figurs out to move one stream to the other soundcard.
At this point, not knowing PA well, he has to assume default setting is NOT working and one has to move every stream over.


Ubuntu is not only for linux geeks, its also for beginners and a little advanced users which *will* have Problems here.
PA wont let you configure it in the first place, it configures itself and chooses on its own, thats the point, and that is wrong, you can argue whatever you want how sophisticated it is and how superb it is.
I agree, its cool. Has nothing to do with the point i am trying to make here tho.
It *can not be* that the upgrade process chooses the soundcard for you and chooses it wrong. PERIOD.

---

### Post by markbuntu on 2009-04-14
So what's your point?
It didn't work for you the way you wanted it to so it is broken?
Or you didn't bother to figure out how to use it so it is broken?

Very few people use two active sound cards and only someone who does will have this problem. And most of those would recognize they are not in a average user situation and so would be more likely to search the forums and learn what they need to know to use and control two sound cards and would also know that they might have to make some changes to the default setup after an upgrade, especially to a beta.

I have two monitors also, should I complain that x is broken because when I installed jaunty the screens were cloned and I had a big desktop in Intrepid?

---

### Post by dandandan on 2009-04-14
My point is let me quote from the last post:

"The Problem with it is, that PA configures it FOR you, in your case right, in my case wrong.
The is no popup asking me which soundcard i want to use, it just uses one, and remembers."

and basically yes, if it does not work it is broken, i think that is the definition.
When sound works in 8.10 and not 9.04 it is broken. Well broken is a harsh word, lets say not working properly.
When *on an upgrade* the upgradeprocess does not carry on with the config form the upgraded from version, there is something wrong.
The updateprocess, if the audio is revamped, should take the alsa config from 8.10 and translate it into pa settings in 9.04, problem solved.

I do understand that 2 soundcards is a bit of an odd config, that does not make it any less broken(or again not working properly) tho, just fewer affected ppl. 

I reported that bug, which clearly is an updatebug to help make jaunty better and make the transition form 8.10 to jaunty easier for all kinds of ppl not just for the mainstream configs. I think the purpose of a beta is to test on a broad horizons on configs.
And yes i do realise that is a beta, THAT IS WHY I AM REPORTING IT HERE AND ON LAUNCHPAD SO THIS ISSUE WONT COME UP IN THE RELASE. doh.

I did *not* report that issue to get condescending "RTFM" posts. 
Following your argumentation, ubuntu devs could leave everything unconfigured, or choose a random config for everything, since everybody can read the forums and learn what they need to know.
One of the first things you learn in coding for example, is to always account for the "less than normal" cases, since those are mostly the ones that break stuff. Just a hint ...
Anyhow, this discussion is getting in a very pointless direction, so i am gonna end it here.
I reported the bug on launchpad and asked for advice here, now its fixed locally, thats all i can do to help other ppl avoid that situation.
Take care.

-dan

p.s. yes you should report that your x or compiz settings wont get carried over, since many many many ubuntu users may not know how to change them and dont want to know.

---

