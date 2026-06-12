---
title: "Natty Narwhal Repositories for T-Bird and F-Fox missing"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by brolin_1911a1 on 2012-10-22
I'm running two computers under Natty Narwhal 11.04, one is 32-bit, the other 64-bit.  At some point during the last two weeks, a alert icon has appeared in my taskbar.  The alert states "Failed to fetch [http://ppa:,launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa:,launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
 E:Some index files failed to download. They have been ignored, or old ones used instead."

Yesterday, I was receiving two such messages, one for thunderbird-stable and the other for firefox-stable.

I went to the indicated URLs and the folders specified are, indeed, empty.

I don't have these entered in /etc/apt/sources.list as such so I'm assuming that they are checked by one of the four default Ubuntu repositories.  What can I do to either remove them so that updates for other packages can continue or remove them from the default list or lists and install the repositories separately?

---

### Post by dino99 on 2012-10-22
open your sources list manager (synaptic or else) and remove that ppa (natty is outdated)

---

### Post by coffeecat on 2012-10-22
> **brolin_1911a1 said:**
> 
I don't have these entered in /etc/apt/sources.list as such so I'm assuming that they are checked by one of the four default Ubuntu repositories.

Not one of the 4 default repositories. The message is telling you it's a ppa repository. It could be that the ppa has removed their Natty packages in anticipation of Natty's end-of-life in a few days. You should be able to find the source file for the ppa in /etc/apt/sources.list.d/ but in a few days you will be getting many more 404s anyway as the principle Natty repositories close down. Time for an upgrade.

---

### Post by brolin_1911a1 on 2012-10-22
> **coffeecat said:**
> Not one of the 4 default repositories. The message is telling you it's a ppa repository. It could be that the ppa has removed their Natty packages in anticipation of Natty's end-of-life in a few days. You should be able to find the source file for the ppa in /etc/apt/sources.list.d/ 

Thanks. I was unaware of where that list was located.  I tried going directly to the mozilla-team ppa but there was nothing there beyond .../ubuntu.  There were no further directories for any distributions.

> **coffeecat said:**
>  ... but in a few days you will be getting many more 404s anyway as the principle Natty repositories close down. Time for an upgrade.

As one who spent three days searching before discovering how to boot 11.04 into "classic" mode, I firmly believe that the word "upgrade" should be in quotes when referring to the later versions of Ubuntu.  I LIKE my Classic 11.04!  On the one computer that I did "upgrade" to 12.04, I ended up installing Linux Mint 13 before the end of the week.

But, if I understand you correctly, I'm going to have to do the same for my two 11.04 machines, complete with all of the reinstalls of the non-Canonical software.  Tell me that's not the case, that there's another alternative.   :(

---

### Post by coffeecat on 2012-10-22
> **brolin_1911a1 said:**
> 
But, if I understand you correctly, I'm going to have to do the same for my two 11.04 machines, complete with all of the reinstalls of the non-Canonical software.  Tell me that's not the case, that there's another alternative.   :(

I'm afraid not. Natty was the last to be built on gnome2 underpinnings, and the classic desktop is gnome2. Gnome2 is dead. 11.10 and later are built on gnome3. If you want the classic gnome desktop, you need to be looking at mate or installing gnome-panel in Ubuntu 12.04 - see the link in my sig for classic gnome in 12.04. Some people are happy with this - others less so. Others are very happy with the Xfce desktop which you get with Xubuntu.

---

### Post by brolin_1911a1 on 2012-10-22
> **coffeecat said:**
> I'm afraid not. Natty was the last to be built on gnome2 underpinnings, and the classic desktop is gnome2. Gnome2 is dead. 11.10 and later are built on gnome3. If you want the classic gnome desktop, you need to be looking at mate or installing gnome-panel in Ubuntu 12.04 - see the link in my sig for classic gnome in 12.04. Some people are happy with this - others less so. Others are very happy with the Xfce desktop which you get with Xubuntu.

Thanks, Coffeecat, both for the replies and advice.

I did manage to install what claimed to be a classic Gnome desktop on my 12.04 machine as well as Xfce.  I'm finding that I like both but there are minor difficulties that I guess I'll have to learn to live with.  One such is the inability to use Synaptic in those.  Synaptic installs, appears to load, and then..... nothing.  But anything is better than that E#&$&$#(&! Ubuntu desktop.

At least now I know what happened to my mozilla Firefox and Thunderbird update directories.

Again, thanks for the answers and advice.  Oh!  And for telling me about /etc/apt/sources.list.d also.  I didn't know about that subdirectory.

---

### Post by coffeecat on 2012-10-22
> **brolin_1911a1 said:**
> One such is the inability to use Synaptic in those.  Synaptic installs, appears to load, and then..... nothing.

That's curious. I can think of no reason why Synaptic should not work in the 12.04 gnome classic desktop. And it definitely works with Xfce. I have it running just fine in Xubuntu, both 12.04 and 12.10.

---

### Post by brolin_1911a1 on 2012-10-22
> **coffeecat said:**
> That's curious. I can think of no reason why Synaptic should not work in the 12.04 gnome classic desktop. And it definitely works with Xfce. I have it running just fine in Xubuntu, both 12.04 and 12.10.

It works on some desktops, not others.  Now I'll have to go through all of them to see which does and does not run synaptic. I'm rebooting that machine now and the options offered are: Default, Gnome, Gnome Classic, Gnome Classic (no effects,) Metacity, Ubuntu, Ubuntu 2D, Xfce 4, Xfce Session, and Failsafe.   I'll just have to boot each in turn to see which runs synaptic and which does not.   I should have done this long ago.

Okay, here are the results of logging in under the various desktops:
Default = desktop background photo but no icons or menus

Gnome (actually Gnome 3) = Synaptic icon among the applications but clicking it does nothing after requesting my password.

Gnome Classic = Synaptic found among Applications/System Tools/Administration.  Requests password and then simply returns to the desktop.

Gnome Classic (no effects) = Same results as Gnome Classic

Ubuntu =  Icon found under &#8220;Dash Home.&#8221;  Asks for password/authentication and then back to Unity  desktop

Ubuntu 2D = Same Results as Ubuntu above

XFCE4 = same as above

XFCE = same results

Terminal window, Ubuntu 12.04 under Gnome and Xfce = 
/home/chris/# synaptic
No protocol specified
(synaptic:6752): Gtk-WARNING **: cannot open display:  :0.0

I rebooted into Linux Mint 13, Cinnamon 1.4 and Synaptic opens and runs with no problems.

---

