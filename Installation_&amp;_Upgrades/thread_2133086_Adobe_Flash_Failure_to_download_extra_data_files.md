---
title: "Adobe Flash Failure to download extra data files"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by chrish8786 on 2013-04-07
Flash has stopped working in Firefox and Chromium Browsers. Help in this forum has been sketchy and uninformed.
Progress so far - 
1. Installed Chrome Browser which gives me Flash again
2. Found Adobe site [http://helpx.adobe.com/flash-player/...sh-player.html]("http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html")
[h=1][FONT=arial]    Identified problem as incompatibility of latest version of Flash 11.06 with Browsers in Linux, should be version 11.02.[/FONT][/h]
Recommendations -
1. Check version of Flash on your own machine, and hope it is version 11.02. Warn other users to refuse any upgrades to 11.06.
2. Post the following message to whoever releases Ubuntu Upgrades. Get your act together. Don't include incompatible upgrades with the routine upgrades. This is a first class catastrophe, Ubuntu has responsibilities to it's users and Ubuntu needs to consider it's self preservation in the Operating System world.
3. Find out if it is possible to get rid of Adobe Flash version 11.06 and reinstall 11.02 without cascading into other system problems.

4. Invite assistance or comments. Any takers.

---

### Post by carl4926 on 2013-04-07
Sorry but this goes against everything I already understand.

---

### Post by claracc on 2013-04-07
> **chrish8786 said:**
> 
Recommendations -
1. Check version of Flash on your own machine, and hope it is version 11.02. Warn other users to refuse any upgrades to 11.06.
2. Post the following message to whoever releases Ubuntu Upgrades. Get your act together. Don't include incompatible upgrades with the routine upgrades. This is a first class catastrophe, Ubuntu has responsibilities to it's users and Ubuntu needs to consider it's self preservation in the Operating System world.
3. Find out if it is possible to get rid of Adobe Flash version 11.06 and reinstall 11.02 without cascading into other system problems.

4. Invite assistance or comments. Any takers.

I cannot understand how you have got flashplayer 11.06 (which is for windows and mac) in your ubuntu system ¿¿??. The only way I can think of you got flashplayer 11.06 installed in your system , but I doubt it is the case,  is through chrome installation. As there is not a chrome .deb in repositories I suppose you'll have use ppa (if there is any) or from a .deb package from google. Better, so you will have to ask for your question to google chrome fora.

I have a fully updated ubuntu 12.04 system and never (repeat never) have received any update to flashplayer 11.06 (between other things because there is not a .deb package for it but an .exe one which is not applicable to ubuntu). I have my flashplugin 11.2.202.275 updated on march,14th,  and it works to see flash videos in web pages. Remark that the support of adobe to flashplayer in linux is limited to security updates only since some time ago.

About number 2 recommendation, what do you mean?, have you received from ubuntu any update to flashplayer in order to install flashplayer 11.06 in your system?. If this is so, you seem to be the only one.

---

### Post by chrish8786 on 2013-04-07
> **claracc said:**
> I cannot understand how you have got flashplayer 11.06 (which is for windows and mac) in your ubuntu system ¿¿??. The only way I can think of you got flashplayer 11.06 installed in your system , but I doubt it is the case,  is through chrome installation. As there is not a chrome .deb in repositories I suppose you'll have use ppa (if there is any) or from a .deb package from google. Better, so you will have to ask for your question to google chrome fora.

I have a fully updated ubuntu 12.04 system and never (repeat never) have received any update to flashplayer 11.06 (between other things because there is not a .deb package for it but an .exe one which is not applicable to ubuntu). I have my flashplugin 11.2.202.275 updated on march,14th,  and it works to see flash videos in web pages. Remark that the support of adobe to flashplayer in linux is limited to security updates only since some time ago.

About number 2 recommendation, what do you mean?, have you received from ubuntu any update to flashplayer in order to install flashplayer 11.06 in your system?. If this is so, you seem to be the only one.
Thanks for the reply. The answer is - No idea. This OS was a clean install of 12.04 last week. I only installed Chrome because Firefox and Chromium would not run Flash. I do not know how to install Flash. I did ask Firefox to look for missing files when it asked for them, but it never found anything to my knowledge. I don't believe that I will be the only one. My other Ubuntu PC has the correct Flash version 11.02 on it.

---

### Post by coldraven on 2013-04-07
I always use Flash-Aid but I just checked and it has been removed from the Mozilla add-ons site.
It can be found on Github but I don't know how you would install it from there.
[https://github.com/webgapps/flashaid](https://github.com/webgapps/flashaid)

---

### Post by claracc on 2013-04-07
This link: [https://github.com/webgapps/flashaid/downloads](https://github.com/webgapps/flashaid/downloads) allows you to download flashaid for firefox

---

### Post by glln0v on 2013-04-07
> **chrish8786 said:**
> Thanks for the reply. The answer is - No idea. This OS was a clean install of 12.04 last week. I only installed Chrome because Firefox and Chromium would not run Flash. I do not know how to install Flash. I did ask Firefox to look for missing files when it asked for them, but it never found anything to my knowledge. I don't believe that I will be the only one. My other Ubuntu PC has the correct Flash version 11.02 on it.

To install Flash Player on Ubuntu you need to install it from the repos. If you tried installing it from the Adobe website, this could explain how your rig got messed up.

To install Flash Player, ensure that you have the **Multiverse** repo enabled (you can do this in Software Sources). Then open a Terminal and input the following commands:```
sudo apt-get update
``````
sudo apt-get install flashplugin-installer
```

---

### Post by chrish8786 on 2013-04-08
Thanks [COLOR=#000000]glln0v. No, I don't believe I have installed Flash directly from the Adobe site. I have done the [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update thing before. Don't remember if it was with this particular install. I have never heard of a repo before. I will do some research and consider the impacts Multiverse repo might have on my system. I no longer apply any suggested solutions without suspicion. 
[/FONT][/COLOR][COLOR=#000000]Thanks coldraven and claracc. I will do some research on Flashaid for Firefox.
Watch this space.[/COLOR]

---

### Post by chrish8786 on 2013-04-10
The version of Flash that Chrome is using is 11.6.602.180. The upgrade of the Flash Installer that went in today was to update to 11.2.202.280. The Flash site above[COLOR=#000000] [/COLOR][http://helpx.adobe.com/flash-player/...sh-player.html]("http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html") does not identify any Flash player in Firefox now. Is anyone interested in this situation?

---

### Post by chrish8786 on 2013-04-13
Is anybody still interested. You have to love this forum, it is real Generation Y. Short attention spans flitting ever onwards to the latest and newest. Like my Chrome Browser which has now updated to Flash version [COLOR=#333333][FONT=Arial]11.7.700.169 and is still going strong. [/FONT][/COLOR]http://ubuntuforums.org/member.php?u=749536 Where are you now? [http://ubuntuforums.org/member.php?u=809261](http://ubuntuforums.org/member.php?u=809261) What wisdom can you offer?

---

### Post by carl4926 on 2013-04-14
> **chrish8786 said:**
> Is anybody still interested. You have to love this forum, it is real Generation Y. Short attention spans flitting ever onwards to the latest and newest. Like my Chrome Browser which has now updated to Flash version [COLOR=#333333][FONT=Arial]11.7.700.169 and is still going strong. [/FONT][/COLOR]http://ubuntuforums.org/member.php?u=749536 Where are you now? [http://ubuntuforums.org/member.php?u=809261](http://ubuntuforums.org/member.php?u=809261) What wisdom can you offer?

What exactly is the problem, it's become obscure to me

---

### Post by lisati on 2013-04-14
Thread closed for review.

---

