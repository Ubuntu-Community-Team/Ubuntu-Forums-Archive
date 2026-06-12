---
title: "Unattended Disc Installation"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by slax on 2014-03-18
Hi Everyone,

I have to prepare an unattended installation, this will be installed on (few years old) desktops, the location of the desktops will be remote minimal/without any internet connection. Due to lack of proper connectivity, i have pack most updated and selective/required applications with the installation disc.

What i am trying to achieve is:
- Should prompt for Options: Installation or Live CD.
- The users will be first time to Linux, so need to find alternative to Dash Home or something which is similar to menu in Linux Mint.
- Rest of the steps should be unattended.
- Should have Multimedia support
- Some Software to Add: Chrome Browser, Google Drive, Open Office, Teamviewer, etc
- Remove software which are not required
- Remove existing Wallpapers, Replace with others
- (If possible) Change Logo (mostly all the places).

This will be CD/DVD version, Kindly help with CD/DVD related help.

Also, Can we squeeze this unattended installation to CD (less than 700MB)?

---

### Post by ian-weisser on 2014-03-18
I don't understand the problem.
Are you asking for help generating the squashfs? .iso? burning the disc?

Do you know which software you consider to be "not required"? You seem to want everything in the existing .iso and more. So it's unlikely you can compress it to CD-size.
Do you really have machines capable of running Unity that cannot boot from a USB? That seems unlikely.

Why are you adding Chrome and Teamviewer and Google Drive to machines that will be "remote/minimal without any internet connection"?

Changing the logo and replacing the wallpaper is not difficult...but once you rebrand away from *buntu, Canonical does not agree to provide security updates and software repositories for free anymore. You can't represent their hard work as your own. See [http://www.canonical.com/intellectual-property-rights-policy](http://www.canonical.com/intellectual-property-rights-policy)

---

### Post by sudodus on 2014-03-18
I agree with *ian-weisser*.

Try an ***Ubuntu OEM installation***, which is portable if you avoid proprietary drivers. I suggest that you keep the Ubuntu logo, but you can certainly change the wallpaper. See this link

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

