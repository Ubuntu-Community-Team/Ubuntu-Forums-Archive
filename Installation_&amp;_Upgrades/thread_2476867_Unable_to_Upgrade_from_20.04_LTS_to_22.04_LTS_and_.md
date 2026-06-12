---
title: "Unable to Upgrade from 20.04 LTS to 22.04 LTS and Dual Monitor Setup"
date: 2022-07-09
forum: Installation &amp; Upgrades
---

### Post by shas-0003 on 2022-07-09
I am trying to do two things

1 Upgrade from LTS 20.04 to LTS 22.04 I get the below error I don't know the resolution path[INDENT=2]
[COLOR=#a52a2a][FONT=book antiqua]Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Hit:2 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease          [/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease              [/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Hit:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease            [/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Hit:5 [http://apt.insync.io/ubuntu](http://apt.insync.io/ubuntu) focal InRelease                              [/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Hit:6 [http://ppa.launchpad.net/yann1ck/onedrive/ubuntu](http://ppa.launchpad.net/yann1ck/onedrive/ubuntu) focal InRelease         [/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease               [/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Get:8 [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04) ./ InRelease [1,604 B][/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Err:8 [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04) ./ InRelease[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]  The following signatures were invalid: EXPKEYSIG B8AC39B0876D807E home:npreining OBS Project <home:npreining@build.opensuse.org>[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Fetched 1,604 B in 3s (515 B/s)[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04) ./ InRelease: The following signatures were invalid: EXPKEYSIG B8AC39B0876D807E home:npreining OBS Project <home:npreining@build.opensuse.org>[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]W: Failed to fetch [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04/./InRelease](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_20.04/./InRelease)  The following signatures were invalid: EXPKEYSIG B8AC39B0876D807E home:npreining OBS Project <home:npreining@build.opensuse.org>[/FONT][/COLOR]
[COLOR=#a52a2a][FONT=book antiqua]W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT][/COLOR]



[/INDENT]
2) The second things is once I upgrade to LTS 22.04 I want to use dual monitors I have the following:[INDENT]DOCK, With Dual Samsung 1080P Monitors
[https://www.ebay.com.au/itm/154594327766?mkcid=16&mkevt=1&mkrid=705-154756-20017-0&ssspo=oqMThpLKQpC&sssrc=2349624&ssuid=meDW621yTZW&var=&widget_ver=artemis&media=COPY](https://www.ebay.com.au/itm/154594327766?mkcid=16&mkevt=1&mkrid=705-154756-20017-0&ssspo=oqMThpLKQpC&sssrc=2349624&ssuid=meDW621yTZW&var=&widget_ver=artemis&media=COPY)

[/INDENT]
I need guidance on both fronts. I have spent numerous hours trying to update the Ubuntu to the latest. Then I am hoping I will be able to use a dual setup with monitors.

Please let me know what I can do I would really appreciate it.

---

### Post by grahammechanical on 2022-07-10
1) Do not upgrade to Ubuntu 22.04 at the moment. The official upgrade path will not be open until the end of September or the beginning of October. If you force the upgrade now you may hit problems.

2) In your list of repositories you have one for Opensuse and the verification key for that repository is invalid.

The software that you installed from OpenSuse might not be compatible with Ubuntu 22.04. That would cause problems with an online upgrade to 22.04. If you remove that OpenSuse repository from your /etc/apt/sources.list file then that error will disappear. You can remove that repository by opening Software and Updates>Other Software and uncheck the box for OpenSuse.

Regard

---

### Post by shas-0003 on 2022-07-10
Thank You That helps me a lot. I will leave it to September, I am not in a rush.

Is there a way to use dual monitors with the Dock I mentioned?. I read that only one monitor is supported from the PC extended directly to Monitor. Does UBUNTU natively support dual monitors. I couldn't find all the settings to Join Screens.

Thanks Again

Regards

---

### Post by itr2401 on 2022-07-14
> Upgrade from LTS 20.04 to LTS 22.04 I get the below error I don't know the resolution path

The OpenSuSE repository you are using is for the 'onedrive' client.

Please review [https://github.com/abraunegg/onedrive/blob/master/docs/ubuntu-package-install.md](https://github.com/abraunegg/onedrive/blob/master/docs/ubuntu-package-install.md) for Ubuntu 22.x installation instructions.

---

### Post by shas-0003 on 2022-07-15
I understand thank you. I will do this. I will remove from repository list.

I am hoping to get some answer on the Dual Monitors, I played around with it but could only extend from PC directly to one monitor. Does Ubuntu allow extension to two monitors with a dock.

---

