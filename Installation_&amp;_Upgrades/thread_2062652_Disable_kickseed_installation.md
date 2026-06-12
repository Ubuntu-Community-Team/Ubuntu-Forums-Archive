---
title: "Disable kickseed installation"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by JSHC on 2012-09-25
Greetings,

I'm deploying Lucid and Precise using Citrix Xenserver 6. As you may or may not know, Citrix comes with built-in templates for installing Ubuntu Lucid/Precise from an Internet source, which is quite nice.

These templates also let you specify boot parameters; as such, I can specify a kickstart file to do installations for me automatically. I do this using the kickstart format; there's no particular reason for this, it's just that I prefer the syntax.

However, my problem is, at the end of the installation, Ubuntu installs a package called 'kickseed' which is causing me headaches. It's not in my kickstart script to install this, but I think that because I'm using kickstart format, it installs it automatically.

I want to disable this because it changes the hostname of my machines to 'kickseed' in /etc/hostname and /etc/hosts. This causes a problem because I have integration with Puppet. The servers initially report themselves as 'kickseed' which is frustrating.

Should I use the preseed format to avoid this? Or is there a way to tell the Ubuntu installer NOT to install that package?

---

