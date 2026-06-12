---
title: "updating RC to Final from Install-CD"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by peletiah on 2005-04-08
hello!

I've installed the RC of ubuntu 2 days ago(RC from 30th of march, it was busy and i could'nt wait for the final release) on a pc with dial-up. now i want to update to the final release of ubuntu, but i'd prefer to update the packages from the final cd rather than via the slow dial-up link(i'm currently downloading the final-cd at work with broadband). i usually work with gentoo, where the install-packages are saved in a folder where portage(the package-building-system of gentoo) saves and looks for the files to install - so is there something similar for ubuntu/apt-get? i also need to update the language-packs for openoffice, thunderbird and firefox, which are english in the current install but should be german after updating to the final version(as it should be on a clean install). to sum it up, my question is: How do i update my RC to the final-version without using the inet but the final-cd? thx for your help!

---

### Post by nicolas on 2005-04-08
you can add the location of the CD in /etc/sources.lst or add cd-rom in Synaptic (Edit -> Add CD-ROM)

Do a reload and now you can add or update from CD-ROM.

Enjoy.

Nico

---

### Post by peletiah on 2005-04-08
perfect, thanks!

unfortunately thunderbird, firefox and openoffice are still in english - how can i change the language of these programs to german? i've already tried to reinstall the german-language-packs with synaptic(nice tool btw) but that didn't change anything(i guess those lang-packs don't apply to non-gnome-programs anyway?!). any suggestions?

another problem i can't find a solution regards the dial-up-modem. i've successfully configured my dial-up with the gnome network tool(system -> systemmanagment -> network) and also added the new 'modem control applet' to the menu, but the problem is that it connects to the internet automatically after logging in with gdm - i'd prefer to start the connection manually by clicking the modem-applet - so where can i change this behaviour? 

thanks again for your help!

---

### Post by thtde on 2005-04-09
[QUOTE=peletiah]unfortunately thunderbird, firefox and openoffice are still in english - how can i change the language of these programs to german? i've already tried to reinstall the german-language-packs with synaptic(nice tool btw) but that didn't change anything(i guess those lang-packs don't apply to non-gnome-programs anyway?!). any suggestions?[/QUOTE]

install language-support-de

---

