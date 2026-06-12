---
title: "Is there a way I can install both gnome and unity and switch between them?"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by david503 on 2017-03-15
Longtime linux admin, first time making the switch to workstation.

Can I install both unity and gnome at the same time and switch back and forth?  I mean not in real time, but with a reboot or something?

I'm assuming apps don't care (or even know) what desktop environment I'm using anyway, right...

So I'm thinking I'll install standard ubuntu with unity, and then after install can I install gnome too? 

And then how would I switch between them?

Thanks guys.

---

### Post by kansasnoob on 2017-03-15
Do you mean GNOME Shell or the GNOME Flashback DE? Flashback tries to look pretty much like GNOME 2. 

I have not tried in 16.10 but Flashback with the Metacity WM works fairly well in 16.04 just by:

```
sudo apt-get install gnome-panel
``` 

That installs all absolutely needed dependencies but you may want to install additional packages to suit your own tastes.

Flashback w/Compiz WM causes major (and possibly unrecoverable) issues with Unity! Themes are sort of a major issue in 16.04 due to the deprecation of settings in org.gnome.desktop.wm.preferences so you're pretty much stuck with Ambiance, although Numix is not horrible. You'll want the package 'gnome-tweak-tool' for manipulating themes in Flashback. I posted a bit about Flashback in Xenial here:

[https://ubuntuforums.org/showthread.php?t=2302432](https://ubuntuforums.org/showthread.php?t=2302432)

Some links to the history behind Flashback here:

[https://ubuntuforums.org/showthread.php?t=2220264](https://ubuntuforums.org/showthread.php?t=2220264)

I recently tried the GNOME Shell DE on top of bog-standard Ubuntu just by running:

```
sudo apt-get install gnome-shell-extensions
``` 

That installs all absolutely needed dependencies - **but be sure to keep using lightdm!**

It didn't break anything (but I had to stick with lightdm as **gdm refused to work**) and I used it for a couple of days before deciding to go back to Unity by logging into the standard Ubuntu session and then just running:

```
sudo apt-get purge gnome-shell gnome-shell-extensions && sudo apt-get autoremove
```

But I made very few modifications (basically just changing to the Adwaita theme). **I suspect if you tweaked more settings you'd end up with a badly borked Unity DE!**

Ultimately** it's better to use just one DE with no expectation of being able to return to the other** - at least not easily. If you want to try the GNOME Shell DE I'd suggest first trying a live USB/DVD of Ubuntu GNOME. If you're more interested in the classic feel of GNOME 2 I'd try a live version of Ubuntu MATE.

---

### Post by tea for one on 2017-03-15
> **david503 said:**
> 

So I'm thinking I'll install standard ubuntu with unity, and then after install can I install gnome too? 

And then how would I switch between them?

Thanks guys.

The short answer is "Yes, you can"

Unity is a user interface built on top of gnome i.e. if you have already installed Vanilla Ubuntu with Unity, you only have to install gnome-shell to have a different (albeit similar) user interface available.

The attraction of gnome-shell is the availability of gnome extensions.

[https://extensions.gnome.org/about/](https://extensions.gnome.org/about/)

You only have to log out and log in again to switch between the two. There is no need to reboot.

Kind regards

---

### Post by david503 on 2017-03-28
Thanks, kansasnoob. Based on that, and my horrible experience with unity, I'm giving up on Ubuntu altogether.  I'll write an extensive review of how horrible the DE (unity) is, compared to even windows 10.  The fact that your post, while I believe it's accurate, is so incredibly complicated, indicates that ubuntu isn't even trying to compete in the desktop OS world. I thought by now after 10 years it would have improved. No, it's worse. Way worse.

Thanks nonetheless.

---

### Post by Autodave on 2017-03-28
I don't agree with that statement. You are trying to do way more than necessary to run a desktop. You don't need all these different desktops going on. You may want them, but you don't need them. I never understood all the fuss over making a desktop look one way or another. Do you do anything on the computer besides look at the desktop? To me (and this is just my opinion) the desktop tells me that the computer is up and running and ready to do something.  I have run Unity, Xubuntu, Lubuntu, Studio, and a few others. While Unity really looks cool sitting there, it doesn't do anything more for me than Xubuntu or Lubuntu, except taking up resources which I would rather have for running programs.

While Unity may not be your cup of tea, dissing it because it is so complicated is just not realistic. You are making it complicated. How far can you modify Win10? How many people have Win10 and hate it? Made for a touchscreen: horrible to use w/o a touchscreen. And I know that many programs have been written to modify Win10. But, it still has to me modified to run with ease. Install Xubuntu and the programs you want. Will it be as flashy a desktop as Win10? No. Will it be more user friendly? Oh yes.

---

### Post by david503 on 2017-03-28
> **Autodave said:**
> I don't agree with that statement. You are trying to do way more than necessary to run a desktop. You don't need all these different desktops going on. You may want them, but you don't need them. I never understood all the fuss over making a desktop look one way or another. .

Err... "all these different desktops going on."  er you mean... 2? Actually I don't even have 2 yet. And as for "looking one way or another", no, it's not just looks, it's functionality.  

> **Autodave said:**
>  
While Unity may not be your cup of tea, dissing it because it is so complicated is just not realistic. You are making it complicated.  

Er... how am I making it complicated?  I have the vanilla install of ubuntu.  And I'm not dissing unity for being "so complicated", I'm dissing ubuntu, underneath, for being so complicated, based on what [COLOR=#000000]kansasnoob described. [/COLOR]

> **Autodave said:**
>  
How far can you modify Win10? How many people have Win10 and hate it? Made for a touchscreen: horrible to use w/o a touchscreen. And I know that many programs have been written to modify Win10. But, it still has to me modified to run with ease. Install Xubuntu and the programs you want. Will it be as flashy a desktop as Win10? No. Will it be more user friendly? Oh yes.

Good to know that about Xubuntu. I haven't tried it. I tried the vanilla standard ubuntu. I'm so crazy like that.

Also- pointing out the problems with win 10 as a justification for the problems of linux DE's is a logical fallacy. "Hey this **** tastes better than that ****."

---

### Post by kansasnoob on 2017-03-29
> The fact that your post, while I believe it's accurate, is so incredibly complicated, indicates that ubuntu isn't even trying to compete in the desktop OS world.

Having not used Windows since 2007, and just recently having installed Windows 10 on four computers, I'd argue that Windows 10 is much more complicated. I had to hunt down numerous "fixes" to get things to behave in a manner that seemed remotely sensible. And quite a few also required that I open a terminal in Windows and run certain commands. But it's all a matter of preference really. Ubuntu offers a great deal of options, some of which are available as "flavors":

[https://www.ubuntu.com/download/ubuntu-flavours](https://www.ubuntu.com/download/ubuntu-flavours)

Once you get used to using the command line, and in some instances Synaptic Package Manager, it's all quite easy. But I'll grant you that change is always hard - especially hard in my case because I'm getting old and I don't like wasting too much time learning new things. I will say that Windows 10 reminds me so much of Windows ME or XP in it's general design that the older desktop environments like "flashback", MATE, Xfce, or LXDE seem quite similar. So in some ways "the more things change, the more they stay the same" :)

---

### Post by cariboo on 2017-03-29
Thread has drifted off of it's original topic. Thread closed.

---

