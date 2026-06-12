---
title: "Software Installer won't install Discord deb"
date: 2023-10-11
forum: Installation &amp; Upgrades
---

### Post by msknight on 2023-10-11
(not sure if this is the right place for the post)

Ubuntu Cinnamon, Jammy Jellyfish 6.2.0-34-generic Cinnamon 5.2.7

After an update and reboot, Discord had an update so I downloaded the latest deb file.

Launching in Software Install, there was no install button and it told me that the deb file was potentially unsafe. The only button I had was a trash can at the top right which I believe is for uninstall.

I had to use dpkg -i to get it install and after this experience, I loaded gdebi because I'm probably going to keep hitting this and I don't want to mess around by dropping to command line every time I need to do a simple deb file install.

In installing gdebi I've had to install other packages I shouldn't really need. Either Software Install can't tell that it was a minor update (0.0.30 to 0.0.31) or else it didn't want to give me the install button because it thinks it's unsafe.

I'm not sure why Software Install was behaving like this, but perhaps the inclusion of an install button which is greyed out would at least tell me why it was behaving like it is, or even the inclusion of a reinstall button would help me get around if it can't tell the version number of the installed software.

Grateful for thoughts and advice please.

---

### Post by ian-weisser on 2023-10-11
Downloading debs that way likely means you lack the key so apt can check that the package is valid.
So Ubuntu Software's refusal to install untrusted software seems appropriate.
Hence your need to fall back to dpkg, which doesn't do that check. 
Or you could add Discord's key, so apt could check and then the Install button would be available.

Complain to Discord for refusing to use any of the many methods to distribute their software securely.
Discord fail. Not an Ubuntu problem.

---

### Post by msknight on 2023-10-11
That's fair. 

It could make it more user friendly with an, "I understand the risks, just do it," button, because there are other ways of doing things... but there's no right or wrong opinion on that I guess.

---

### Post by ian-weisser on 2023-10-11
Polite quibble: Right and wrong seem fairly clear here.

Right: Use the safe, trusted distribution channels, some of which are over 20 years old.

Wrong: Send users a deb file from an untrusted source
Wrong: Send users a deb file and expect them to figure it out.
Wrong: Ask users to install unsigned, unverified software.

Let's not reward Discord's incompetence.

---

