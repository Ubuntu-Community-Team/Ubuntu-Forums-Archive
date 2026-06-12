---
title: "Jaunty installation ALSA and Nvidia solved"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kzipz on 2009-03-05
Here is my experienes and guide of how I did it finally WITHOUT any headaches or hassles FINALLY.

In previous attempts to configure my Dell XPS 1730 (2 previous attempts with Jaunty 9.04 r3) I ran into some problems getting full performance from my *dual* Nvidia 8800m gtx gfx cards.

I'm also a music head and use my laptop to record so SOUND is my major issue. I have also run into the 'alsa noise' bugs that are commonly experienced. 

Another problem I had was getting the eye candy to please me with a balance of enjoyable graphics and low resource consumption. I'm not a big 3D gamer but I'm severly addicted to GL screensavers. So I think I'm as critical of video performance as those with 'half-life' habit. Being not so light of heart...I've plunged into the land of the wild wabbit and started working with a Jaunty installation. 

During my second attempt at installing I began to have problems with the sound when rebooting. It happened after I had installed several packages from synaptic and I didn't notice the problem at the moment it happened. On a reboot it became apparent and when I tried to troubleshoot 

I stopped...after 4 hours of reading and applying fixes when I ran into lib6c synaptic freeze in the middle of installing 'ubuntu-restricted-extras' 

ON reboot KERNEL panic. But I didn't...just made a decision I was going about it wrong...so I backed up. And made a new plan... it went like this;

8:35pm -- [LIST]
[*]Start fresh install using entire drive(200gb)
[*]       reboot- after installation completes
[*]       edit repositories- /etc/apt/sources.list to reflect chosen repo(speeds things up)
[*]       Drop to term-(Alt+F4)
[*]       Stop GDM- sudo /etc/init.d/gdm stop
[*]       update repos- sudo apt-get update 
[*]       upgrade system- sudo apt-get upgrade 

[*]       reboot- after upgrade completes
[*]       downloaded updated driver NVIDIA 1.80.29 release [how to instructions found here]("http://www.nvidia.com/object/linux_display_amd64_180.29.html")
[*]       Drop to term-(Alt+F4)
[*]       Stop GDM- sudo /etc/init.d/gdm stop
[*]       Install driver NVIDIA 1.80.29

[*]       reboot- 
[*]       downloaded ALSA upgrade script [how to instructions found here]("http://ubuntuforums.org/showthread.php?p=6589810")

[*]       reboot- 
[*]       Drop to term-(Alt+F4)
[*]       Stop GDM- sudo /etc/init.d/gdm stop
[*]       update repos- sudo apt-get update 
[*]       install ubuntu-restricted-extras- sudo apt-get install ubuntu-restricted-extras[/LIST]

Now I added my personal choices for eye candy- cairo-dock, emerald, compiz-settings-manager, compiz-extras along with some gnome and gtk themes. 

I've moved from Avant windows navigator to cairo-dock because of the incredibly simple and extensive configuration that cairo-dock offers. I chose the svn installation as a matter of personal choice. I found that this version stable and easy to load using the instructions [I found here]("https://help.ubuntu.com/community/CairoDock"). There are also instructions on installing it in the traditional methods.
I followed the same pattern of dropping to terminal and stopping gdm before installing Cairo-dock.

After it completed installing with no error I rebooted, logged in and ran update from the desktop.

1:35am --100% SUCCESS.

ALSA sounds clear as a bell, graphics are smoking and so far no crash messages or errors that come to the fore. Time will certainly tell...but this whole operation went faster than my other attempts at loading the same exact software...mainly because I spent 0 time on troubleshooting. 

**[COLOR="DarkGreen"]PLEASE:[/COLOR]** [COLOR="DarkOliveGreen"]take a moment to post a result *if you try this method*. confirmation of these results would help everyone.[/COLOR]

That was a major benefit of doing all of the upgrading of the audio and video with the gdm stopped I think. I'm not old school linux...more on the unix side...but my observation is that the OS does a better job when the resources being changed are NOT in use.

Hope this post helps one person save a little more time to play-me, I'm heading for the sandbox now- yeehee

System:
Dell XPS 1730
2 x Nvidia 8800m-gtx
Intel sound
4 gb ram
2 x 200 gb 

Linuxmint 6
Jaunty Desktop AMD64 9.04 rc3

NO WINDOWS

---

### Post by kzipz on 2009-03-13
bump

---

### Post by kzipz on 2009-03-23
I finally threw in the towel on tweaking my notebook with Ubuntu standard and went to the OpenGEU distro for x64.

I don't understand why it went so smoothly. :?: .but it did. As far as I can find on the forums I may be the first to 'slide' in the nVidia proprietary drivers without any burps. 

[Check out these basic instructions]("http://ubuntuforums.org/showthread.php?p=6941103#post6941103") and follow links for the download links and further instructions on tweaking the pulseaudio settings once you get the rt kernel up with nvidia running.

I don't know if this will work on other distros on a clean install but DIDN't work for me when I tried on Ubuntu.(Jaunty or Inrepid)


Good luck and enjoy pumping up the volume!!!:guitar:

Kz

---

