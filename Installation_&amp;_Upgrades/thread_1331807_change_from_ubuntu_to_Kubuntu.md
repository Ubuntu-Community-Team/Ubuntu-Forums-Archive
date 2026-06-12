---
title: "change from ubuntu to Kubuntu"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by pearldrums on 2009-11-19
[COLOR=DarkRed]**EDIT: I meant to say Xubuntu not Kubuntu...** **I know that makes this thread very confusing given what is written in the subject line. I'm not sure there is anything I can do to fix that, sorry.**[/COLOR] 

If I were to want to change from Ubuntu installed on my notebook to Kubuntu, would I be required to do a fresh install. I know when I was toying with the Netbook Remix I could just swap out some packages. Would this be an extensive project, or a simple one?

thanks!

---

### Post by coffeecat on 2009-11-19
Quite a simple one. Simply install the meta-package 'kubuntu-desktop' either with Synaptic or with 'sudo apt-get kubuntu-desktop'. You'll then have both the kubuntu and Ubuntu (gnome) desktops installed. You can choose which one to work in at the login screen by clicking on 'options'. And you can set either as the default.

Disadvantages: it's a fairly hefty download and will consume over 1GB on your HD. Also, you'll have a load of KDE apps in your Gnome menus and Gnome apps in your KDE menus. Some people don't like this. I don't know why. 

**Edit:** just noticed that you said 'change'. The above, of course, gives you the choice of KDE and gnome. If you want to replace gnome with KDE it is possible in theory, but a bit of a long haul. If you have sufficient HD space, why not go for both? For instance - in the dim and dark days of yesteryear :wink: when I was using Suse 9.3, I had both KDE and gnome installed. Depending on my mood I'd log into either. 'It's Saturday - it must be Gnome today.' :)

---

### Post by pearldrums on 2009-11-19
heh, i made a little mistake, I meant to ask if I could change to Xubuntu (not Kubuntu). I checked synaptic and see the Xubuntu meta-package. Would I know that KDE programs are a little different than Gnome, but I don't know much about Xfce. Would the transition (between apps, settings, etc) be easier or harder to do thank KDE?

---

### Post by snowpine on 2009-11-19
It's very easy to remove Gnome (Ubuntu) and install KDE (Kubuntu) in its place:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

(edit) or Xfce (Xubuntu)

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

You could also switch between all three for a while while you're deciding which you like best.

---

### Post by coffeecat on 2009-11-19
> **pearldrums said:**
> heh, i made a little mistake, I meant to ask if I could change to Xubuntu (not Kubuntu). I checked synaptic and see the Xubuntu meta-package. Would I know that KDE programs are a little different than Gnome, but I don't know much about Xfce. Would the transition (between apps, settings, etc) be easier or harder to do thank KDE?

No problem. As you've found, just install the xubuntu-desktop metapackage. This will give you the Xubuntu-ised version of Xfce, just as Kubuntu-desktop gives you the Kubuntu-ised KDE rather than the vanilla one.

Since Xfce uses the much of the same gtk libraries as gnome, the appearance of Gnome packages in the Xubuntu menus and vice versa is less intrusive than with KDE/Gnome. And I guess the download will be less than for Kubuntu-desktop. So - install Xubuntu-desktop and you should be able to choose Xfce or Gnome from the login screen just as I described for KDE/Gnome.

There is another way. :) There is an excellent UK-published magazine called Linux Format. It is available in most countries, but might be hard to find. A couple of months after each release of Ubuntu, the magazine puts a special installable version of Ubuntu on the cover DVD. It includes the gnome, KDE and Xfce desktops and a sizeable range of included apps. It's a hefty size, of course, but popular with LXF readers. You might want to look out for it.

---

### Post by pearldrums on 2009-11-19
sweet, now I've got Xubuntu up and running, and I must say so far I like it (but thats not saying much). I've got a slight problem though. I was trying to move some of the applets around the panels and everything on the right side of the top panel ended up oriented on the left side and I cannot change this. I can change their order, but I cant put them on the right side. There is also the gnome power manage and the Xfce power manager.

Right now I messed up both pannels, is there an easy way to just go back to the default config? If not can I at least get everything back on the right side?

---

### Post by pearldrums on 2009-11-19
well, I've figured most of this out, but I'm going to write it down for anyone who might find this looking for information.

in the Xfce enviornment you will automatically end up with your applets/launchers on the left side unless you add an expanding space. Go to "add new items" then "separator or spacing" and add it. You can adjust its properties as you wish, but your probably looking for an expanding empty space.

The issue with the power manager is a leftover from Gnome as I have not deleted the Gnome Desktop. It is located in the notification area. Unfortnuately the notification area does not have a handle to adjust the properties or move that I can see. However, you can adjust what shows up by un-checking them from the "session and startup" options (Applications -> settings -> session and startup)

I would still like to be able to put a handle on the notification area, but until then you can just move everything around it. If you want to change which panel its on you have to remove it and then add it again. To do this right click a panel, click "add new items" and then drag anything from the notification area to the "add new items" window. It will ask you if you really want to do this. Click yes. Then you can re-add it to a different panel in a different place if you'd like. 

One thing I'm still having issues on is adding launchers. Its completely possible, but where as ubuntu has both "custom application launcher" and "application launcher" xubuntu only has "launcher" which requires you to do more leg-work and I don't know how to get the nice looking icon yet.

---

### Post by Rifester on 2009-11-19
So if you add the KDE desktop to your gnome ubuntu does it effect your system at all?   Does Ubuntu get buggy?  I have been wanting to play with KDE/Kubuntu and tried dual booting, but can't get the wireless to work in Kubuntu.   If I decided to remove the KDE desktop would it remove completely and not mess with my current setup?   I have rebuilt my system and clean installed too many times over the last few months, but id I could use KDE and gnome that would be awesome.   Is anybody actually jumping back and forth between desktops like this? What is your experience?

---

### Post by pearldrums on 2009-11-19
> **MRife said:**
> So if you add the KDE desktop to your gnome ubuntu does it effect your system at all?   Does Ubuntu get buggy?  I have been wanting to play with KDE/Kubuntu and tried dual booting, but can't get the wireless to work in Kubuntu.   If I decided to remove the KDE desktop would it remove completely and not mess with my current setup?   I have rebuilt my system and clean installed too many times over the last few months, but id I could use KDE and gnome that would be awesome.   Is anybody actually jumping back and forth between desktops like this? What is your experience?

Actually I'm using Xubuntu not Kubuntu (i'll make an edit on my top post to be less confusing), but yes I am able to jump back and forth with the greatest of ease. There are a few things that seam peculiar because of the parallel install, but the functionality and stability do not seem to be effected.

I am left wondering about one thing though, I tried running Xubuntu on a jump drive first and it showed that when fully charged my battery life should be around 5 hours. Now when its installed over gnome it shows that I should have around 3 hours 40 min. Is this because it estimates this from past data and the current data does not reflect the new settings. Does anyone know why else this could be happening? This is a major reason for me switching to Xubuntu

---

### Post by Robertjm on 2009-11-20
Basically just sucks up a whole LOT of space is the biggest issue I know of.

When you launch your computer you'll have the choice of which GUI you want to load.

One annoying thing about KDE is you get lots of packages you may not want. Personally I use Open Office, but if I went to uninstall KOffice it would uninstall KDE too!!!

> **MRife said:**
> So if you add the KDE desktop to your gnome ubuntu does it effect your system at all?   Does Ubuntu get buggy?  I have been wanting to play with KDE/Kubuntu and tried dual booting, but can't get the wireless to work in Kubuntu.   If I decided to remove the KDE desktop would it remove completely and not mess with my current setup?   I have rebuilt my system and clean installed too many times over the last few months, but id I could use KDE and gnome that would be awesome.   Is anybody actually jumping back and forth between desktops like this? What is your experience?

---

### Post by Rifester on 2009-11-20
Wow!   I wish I knew I could have done this months ago.   Thank you very much.   I was up late last night setting up KDE for myself and my wife.    I accidentally deleted the bottom tool bar and kicker icon on the bottom left.   I cannot figure out how to get it back (as I am new to KDE as of now).   Any suggestions?

---

### Post by coffeecat on 2009-11-20
With the 3.* series of KDE, if you got in a complete muddle with the desktop settings, you could simply delete the ~/.kde folder and contents, log out and back in again and a new ~/.kde folder would be created with all the default settings. Which means you lost any personalised settings you'd made since install, but at least you got your desktop back.

I believe you can do the same with KDE 4.*, but as I've only briefly played with 4.*, I can't guarantee anything - confirmed Gnome man here. :wink:

If you want to try this, instead of deleting ~/.kde you could rename it to something like ~/.kde.backup, so that if everything went pear-shaped, you could revert back.

But hopefully a proper KDE user will happen by and tell you if there's a simpler way of getting those bits back.

---

