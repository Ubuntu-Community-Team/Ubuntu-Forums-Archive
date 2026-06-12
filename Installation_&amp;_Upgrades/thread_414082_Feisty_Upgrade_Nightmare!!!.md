---
title: "Feisty Upgrade Nightmare!!!"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by W@LT on 2007-04-19
Having made the mistake of installing the Feisty beta version some weeks ago and suffering no end of problems I startyed agai and re-installed from scratch the 'Stable' release of Edgy... No problems and I had just taken the plunge to ditch Vista in favour of Ubuntu...

I therefore decide to wait ptiently for the official 'No warts' vesion of Feisty

Nightmare!!!!!

I have had no end of problems and as I sit here now I am cataloguing the numerous error that seem to be being diplayed..

First I got a message that certain programs could not be installed and that the system might be un-stable

The sytem then froze!!

After threee reboots managed to get Ubuntu to load 

I now have another set of errors

[COLOR="Blue"]
NVidia Glx issuesdev failed to install

subprocess pre-installation script returned error exit status

conflicting packages - not installing nvdia-glx[/COLOR]

conflicting packages - not installing libgl1-mesa-d

conflicting packages - not installing mesa-common-dev

E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing mesa-common-dev

From the rest of the post on this forum it looks as if I am not the only one...

I never had this problem with my Vista upgrade...

What the hell is happening here??

---

### Post by eentonig on 2007-04-19
First off all. Stupid to rush in on the same they that everybody else is trying to rush for theis copy.

Second. How did you install? Completly fresh install from the live cd? Did you check the CD for errors?

---

### Post by W@LT on 2007-04-19
Upgrade was from the Update Manger 

Hit the button and off it went..

I presume you are suggesting that the new release in not fit for purpose... So why release the version??

Surely it would have been better to delay for two more weeks than to subject other to this apparant nightmare...

Posting this using MS Vista.... working fine :)

I guess another re-install of Edgy will have to be done.... This is getting tedious !!!!

---

### Post by eyelessfade on 2007-04-19
Well if few people test beta we can't find all bugs, and they pop up after release. Second all I know who upgraded today report few or none problems at all.

But on your problem, why do you have the nvidia-glx-dev package installed. Remove and try to reinstall nvidia-glx

---

### Post by W@LT on 2007-04-19
I cannot beleive no problems

However will remove NVIDIA ....

Now how do I do that?

---

### Post by eentonig on 2007-04-19
Well, If you're upgrading on an already modified system... how can you blame Feisty? They can't take into account every possible setup John Doe can make.

---

### Post by fickleflame on 2007-04-19
> **W@LT said:**
> Upgrade was from the Update Manger 

Hit the button and off it went..

I presume you are suggesting that the new release in not fit for purpose... So why release the version??

Surely it would have been better to delay for two more weeks than to subject other to this apparant nightmare...

Posting this using MS Vista.... working fine :)

I guess another re-install of Edgy will have to be done.... This is getting tedious !!!!

I'm wasn't aware that upgrading via the update manager was supported. I believe the upgrade documentation said to use a Feisty CD to do the upgrade. I'm still waiting for my download of feisty to finish, but it sounds like you should re-visit the install method you used. From your earlier post it wasn't clear if your edgy install was clean or had you installed other packages before you tried to upgrade?

btw, you cant really compare a Linux upgrade to Vista. If you visit any Microsoft support sites you'll notice that there is no end to issues with XP to Vista upgrades.

---

### Post by eyelessfade on 2007-04-19
> **W@LT said:**
> I cannot beleive no problems

However will remove NVIDIA ....

Now how do I do that?

apt-get remove nvidia-glx-dev
apt-get install --reinstall nvidia-glx

---

### Post by W@LT on 2007-04-19
Looks like I am the only one then!!!

I ran Update manager and at the top of the screen in mentioned the Upgrade was available and I clicked it and off it went...

Am I the only one with this enabled?.. I am honoured..:)

It recognised other 'Non Standard' packages ... Envy and Automatix but said it would disable them and I could enable them after the install

Still it didn't work and the problems are real...

Maybe I will wait for another 3 months for the  'Stable' version is ready for download... and then it it 'Funky Gibbon' to look forward to... oh joy :)

So...How do I remove the Nvidia-dev-glx package now it will not re-boot..

---

### Post by Drezliok on 2007-04-19
If you used Envy to install your drives you have to use envy to uninstall them then remove envy, it's not for Feisty Fawn

Amd it will be Gusty Gibbon

---

### Post by W@LT on 2007-04-19
IT WILL NOT BOOT UP!!!


Did the upgarde warn of impending problems... NO!


Now what??

---

### Post by Lucifiel on 2007-04-19
Hmmm... if you can, I suggest downloading Feisty through the torrents and then burning it. Forget about upgrading since it's often error-prone.

---

### Post by W@LT on 2007-04-19
Thanks

Run

apt-get remove nvidia-glx-dev
apt-get install --reinstall nvidia-glx

here are the results when booting into recovery menu

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I thought recovery booted into root

any other ideas?

---

### Post by eyelessfade on 2007-04-19
So it wasn't a feisty problem after all.
The ubuntu dev team have stated many times that envy and automatix can make the system useless.
last problem might be because the hard drive is mounted read only.

A clean install of feisty might be a good ide now. An experienced linux user should be able to fix this easy. But it takes time :)

---

### Post by jcconnor on 2007-04-19
Just a thought but did you try sudo apt-get?

---

### Post by DarkStarAeon on 2007-04-19
> **eyelessfade said:**
> 
The ubuntu dev team have stated many times that envy and automatix can make the system useless.
 


uh oh... Envy was the only way I could ever get my graphics card to work with 6.10, I had tried everything else first. So, I'm hoping nothing breaks. By the way, on the site for Envy it says it works for Feisty too, but, it also says "unstable"...hmmm.

I have Automatix, but I don't think I installed anything with it. 

Upgrades always make me nervous.

I really hope I don't have to do a clean install, I spent soooOOo much time configuring Edgy the way I wanted it.

---

### Post by eyelessfade on 2007-04-19
fingers crossed :)

you could remove envy first and the graphic modules.
But then you would have to upgrade from console. By the way what graphic card do you have?

---

### Post by davidvasta on 2007-04-19
There is a new verion of Envy out, but you should be able to get the nvidia drivers out and just use the one with Ubuntu and install the dirty version of Envy later.

I upgraded ENVY before I upgraded Ubuntu. I hope that helps things. If not I will just remove it and install it again. I have an Nvidia 6800XT AGP Card. I know the ATi cards are having more trouble and Albert from ENVY is working on the ATi stuff but he knows right now that it's kind of weak. Check the Planet for his post.

---

### Post by DarkStarAeon on 2007-04-19
> **eyelessfade said:**
> fingers crossed :)

you could remove envy first and the graphic modules.
But then you would have to upgrade from console. By the way what graphic card do you have?

Yeah I can't do any of that now though, the upgrade is fetching files for feisty. argh hindsight! lol

I have the nVidia 7300LE.

Question:

I have Automatix, and looks like I did use it to get Google Earth, think that will be a problem?

---

### Post by DarkStarAeon on 2007-04-19
> **davidvasta said:**
> There is a new verion of Envy out, but you should be able to get the nvidia drivers out and just use the one with Ubuntu and install the dirty version of Envy later.

I upgraded ENVY before I upgraded Ubuntu. I hope that helps things. If not I will just remove it and install it again. I have an Nvidia 6800XT AGP Card. I know the ATi cards are having more trouble and Albert from ENVY is working on the ATi stuff but he knows right now that it's kind of weak. Check the Planet for his post.

I should have done that, didn't even think to upgrade Envy first, doh!

Now I'm int he middle of this upgrade, so can't do anything.

I really should have stayed away from the computer today, 2 hours sleep and coffee isn't helping much. Otherwise I would have thought this out better first before deciding to upgrade.

I just grabbed the new version of Envy from the site, saved it to a thumb drive. Not sure how I would get it installed if X crashes? Hmmm.

ah well, we'll see what happens I guess, lol

---

### Post by davidvasta on 2007-04-19
> **DarkStarAeon said:**
> I should have done that, didn't even think to upgrade Envy first, doh!

Now I'm int he middle of this upgrade, so can't do anything.

I really should have stayed away from the computer today, 2 hours sleep and coffee isn't helping much. Otherwise I would have thought this out better first before deciding to upgrade.

I just grabbed the new version of Envy from the site, saved it to a thumb drive. Not sure how I would get it installed if X crashes? Hmmm.

ah well, we'll see what happens I guess, lol

I did since I have had trouble in the past with it during kernal upgrades. I have had to remove ENVY and resintall it, but it's no big deal. Feisty has nVidia drivers built in and should pop to it once you take out all the nVidia Stuff.

---

### Post by DarkStarAeon on 2007-04-19
Yeah I had that same problem during kernal upgrades. I just typed in "envy" after X got done letting me know it crashed and envy took care of it. I hope it does again. yipe.

**I just tried to uninstall a game from add/remove programs and got this error:**

[quote]E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/qoute]

I'm not sure what that means, but I have an impending sense of doom.

Granted, the upgrade is still fetching files, but that still makes me nervous.

Anyone know what that error means?

---

### Post by radioactivebug on 2007-04-20
If you're using the update manager and at the same time trying to add/remove a program, you're not going to be able to access all the neccesary files. Some of them are locked because they're in use, that's what that error is from. So just let the update finish then try again.

---

### Post by DarkStarAeon on 2007-04-20
ahh. ok. thanks. :)

---

### Post by W@LT on 2007-04-20
OK...

Feisty is now up and running... Managed get PC to boot into Ubuntu (Don't ask me how) and then the Update Manager said that I had some 465 files to downlaod which related to a failed upgrade..!!!

I only have one Upgrade file that will not load...NVIDIA-GLX... this is the one that caused some of the issues yesterday

If I try to upgrade to the new file it gets as far as unpacking and then  get the error:

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status

If I can fix this I think I could have a working version of Feisty (Technically that is)

Any Ideas ????

Thanks for all your perciverence and help so far... but things get very frustrating when 'Oven Ready' relase upgrades cause so much grief.

I do hope the other guys on here have upgraded theirs OK..

---

### Post by W@LT on 2007-04-20
:)

---

### Post by DarkStarAeon on 2007-04-20
> **W@LT said:**
> OK...

Feisty is now up and running... Managed get PC to boot into Ubuntu (Don't ask me how) and then the Update Manager said that I had some 465 files to downlaod which related to a failed upgrade..!!!




Umm, I'm just guessing here, but if you had that many files to download because of a failure in the upgrade process, it sounds like you restarted your computer before it had retrieved them all.

While I was upgrading I'd get an error message about every 300 files or so, and I'd have to close that error dialog, then go to the update manager, click the upgrade button again, and it would pick up where it left off in the fetching files process. Had I restarted my computer without fetching all the files, I think it would have caused similar issues.

Again, not saying that's what happened, just saying it sounds possible.

Yeah graphics drivers are often a pain, not sure how to fix that, sorry.

Seriously though, I've had issues with upgrading Microsoft products too, look at their site, millions have had issues upgrading things, installing things etc. At least with Ubuntu you didn't have to call tech support and ask them to give you a new license key because your perfectly good one doesn't work anymore for no good reason. That always made me mad with MS.

Hope you get your graphics drivers issue resolved.

---

### Post by W@LT on 2007-04-20
Thanks for the reply...

The cool thing is that everything seems to be working fine!!

NVIDIA is working a treat...

It's just soooo annoying having this blasted 'You have 1 Update' sitting at the top of the screen :) 

I was wondering if at this stgae I could delete something and make it go away ..

At this point it's a matter of aesthetics and not functionality that is bugging me...

Am I getting too picky?      :rolleyes:

PS... Love the pics of your desktop... realy cool

---

### Post by DarkStarAeon on 2007-04-20
Cool, glad everything is working fine now :) 

Yeah, it's a little picky, but I know what you mean, it's annoying when something just hangs there and won't go away or do what it's supposed to. Maybe try it again in a few days?

Oh, thanks :) Yeah let's just hope my highly customized theme doesn't break when I finish this upgrade, lol, I'm still fetching files, since yesterday about this time. Servers are still slammed I guess.

---

### Post by odin1965 on 2007-04-20
"It recognised other 'Non Standard' packages ... Envy and Automatix but said it would disable them and I could enable them after the install"

  Automatix is unsupported and is known to break the distro upgrade process. This is probably especially true with Feisty as it comes with it's own method for installing codecs and drivers.  
  You should fresh install using the desktop CD. I know this seems like a step backwards, but it is the best way.

---

### Post by anachreon_ on 2007-04-20
Hey guys, it looks like most of your problems are more or less solved for the moment, so I just wanted to add one observation.  

I've found, in the past 6 months of using ubuntu (I've ditched windows completely, and will never go back) that it's actually quite important to get comfortable in the console.  I know it can be a hard switch to make.  Windows sort of babies you into not actually knowing how your computer works.  

I used to have problems installing / removing / upgrading packages because, at least in Kubuntu, the graphical package manager can get messed up and there's really no way to fix it graphically.  If I can give you one piece of advice, it is to learn how to use the "apt-get" and "dpkg" command line programs.  You can basically fix EVERY package problem you have using these two tools.  For example, if a package doesn't get set up correctly in Adept (KDE's package manager) you can often solve the problem using the "sudo dpkg --reconfigure -a" command, or checking which package is causing the problem, and just doing a manual reinstall with "apt-get install."  

Anyway, if you google either, there's plenty of info on the net about them.  It's how I went from being totally clueless to having no real problems anymore.  When I upgraded to Feisty today I had some predictable hiccups (mainly with the nVidia proprietary driver - I hadn't downloaded the unstable version of the Envy script for Feisty).  All of them were fixed easily enough using dpkg.

Hope I'm not sounding preachy or anything - good luck with your upgrade!

---

### Post by W@LT on 2007-04-21
If I run the CD upgrade over the top of the existing install do I lose everything as I have set up at the moment or dies it keep the current settings etc?

---

### Post by aeon on 2007-04-21
> **W@LT said:**
> If I run the CD upgrade over the top of the existing install do I lose everything as I have set up at the moment or dies it keep the current settings etc?

As long as you don't overwrite anything in your /home/$USER folder everything should be ok, pretty much all your settings are stored under/home/$USER/.gnome or .kde or which ever DE/WM you use

---

### Post by Seti on 2007-04-21
Sometimes I feel more at home in /home/$USER than anywhere else. Familiar territory. Interesting  how as software gets better and better, we become more demanding of it, like, why isn't it just installing my favorite bootloader by default anyway?


Thanks for spoiling us Feisty...

---

### Post by W@LT on 2007-04-21
Thanks for the reply...

Have tried again today but still getting the error shown below against the NVIDIA-GLX upgrade

:E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2

I am sure someone must know how to resolve this issue... maybe one of the superuser guys who came up with UBUNTU / this upgrade?

Apart from that all is well and the migration from MS Windows (Vista) is almost complete

I still have to boot up into Vista for all my MS Money 2000 entries and the odd DVD Backup... but hey.. I feel so liberated :lolflag:

---

### Post by Derspankster on 2007-04-21
Yes, EVERY distro upgrade is a COMPLETE NIGHTMARE in regards to Nvidia drivers. I'm broke right now, had to revert back to an old card Nvidia 4000 and the generic nv drivers. I'm sick to death of this. Tried Envy when I was going through a similar issue with Edgy and it broke the system. I've typed sudo dpkg-reconfigure xserver-xorg so many times I'm sick of it. Ubuntu upgrades are a thousand times more frustrating than Windows updates.

---

### Post by W@LT on 2007-04-27
I still cannot get rid of the erro on the upgrade that is sitting waiting to be loaded!!

Have tried again today but still getting the error shown below against the NVIDIA-GLX upgrade

:E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2

!!!!!!!!!!!!!!!!!

---

### Post by GuiGuy on 2007-04-27
> **W@LT said:**
> Looks like I am the only one then!!!.

No you are not.

I tried "upgrading" my wife's stock standard Edgy box today. It fell over big time so I restored the backup image.

BTW, I find those who argue that it is ok to mark an upgrade as 'stable' and then sit back and wait to see who reports what problems as disingenuous at best. IN fact, it sort sounds like something M$ would do.

Regards

PS- Always make a backup image before mucking about with linux.

---

### Post by DarkStarAeon on 2007-04-27
Only thing I can think of is try Envy man, sorry I can't be of more help. Envy is the only thing that has worked for me when it comes to graphics drivers.

I think you'd have to download and install Envy, then remove your current graphics drivers, log out, then when you get the black screen after X throwing a fit, login and type in: Envy.

Don't quote me on that.

---

### Post by DarkStarAeon on 2007-04-27
> **GuiGuy said:**
>  
PS- Always make a backup image before mucking about with linux.

That goes for any OS or distro really. Unless you like potentially setting yourself up for disaster.

I never had any problems installing Windows, but I certainly had problems with it after that.

---

### Post by W@LT on 2007-04-27
OK.... wish me luck

I am going to have a stiff drink and then de-install the drivers using Envy and then re-boot and install them again

If you don't hear from me again... I have failed and gone back to the 'Stable' version of Vista - no driver issues.. NVIDIA drivers auto loaded etc... :) 

If nothing else... at least it keeps the topic live and warns others of the potential problems with the upgrade to 'Fishy'.. sorry 'Feisty'

I would like at this point to copy a comment from earlier posting in this thread which said:

*"All I know who upgraded today report few or none problems at all"*

I only wish I knew YOU before I started the upgrade to Feisty

Let's hope 'Funky Gibbon' is released with a bit more beta testing....

---

### Post by DarkStarAeon on 2007-04-27
Hmm, so did you make it back via Ubuntu and forget to post, or did you go back to using Vista?

---

### Post by W@LT on 2007-04-27
Hey... I am a die hard....

Still got the GLX error... but I think I am going to have to live with it..

Now working on my LapTop (Sony Vaio) with ATI Mobility Radeon 9200 on-board

Fishy upgraded reasonably but defaulted to VESA ....and it didn't like the ATI drivers.

Have spent a few hours getting this going.... But now it is working realy well

OK...Time now to catch up on an old episode of Dr Who :)

---

### Post by DarkStarAeon on 2007-04-27
Welcome back!

ATI? ahhh, yeah, never had any luck with ATI, if you run any flavor of linux you really ought to consider using Nvidia, usually much more stable.

At least you got it running well.

If there is a Linux Users Group in your area you may want to consult them for help on getting rid of the error.

---

### Post by W@LT on 2007-04-30
Just another update..

Laptop working better than ever... espcially after enabling some of the 'Tweaks' I found on a web site... Machine is running faster than ever.. so is the broadband :)

I also did a upgrade of my wifes DELL machine yesterday...

No problems at all and Beryl is working a treat!!!

Either I am getting better or the using the true upgrade / Install disk has most bases covered...

However upgrading my sons Sony PCV-W1 desktop is proving a chore... I can't get the onboard SIS graphics card to work with Beryl!!

Two more PC's to go and then I am there.

---

### Post by DarkStarAeon on 2007-04-30
Good that all is going mostly well. Ack, Sony's, never had any luck with them.

Well, I upgraded my wifes computer, which went pretty quickly as far as downloading went, and it installed flawlessly, but man does it take forever to boot up. Once it does though it works fine.

---

### Post by W@LT on 2007-05-01
Now isn't that strange..

My wife computer takes an age to boot up too ....:confused: 

Maybe it's a womens thing!!!

---

### Post by DarkStarAeon on 2007-05-01
Whatever it is, it's irritating my wife.

---

