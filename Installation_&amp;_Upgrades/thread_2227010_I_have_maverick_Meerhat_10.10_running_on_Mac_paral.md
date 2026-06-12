---
title: "I have maverick Meerhat 10.10 running on Mac parallels, how do I upgrade?"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by Louise_Avon on 2014-05-30
I tried upgrading with using Terminal with commands below. When I restarted the VC it informed me that kernal parts where missing and needed to reinstall my parallel tools. Although I seem to have a desktop screen, I could not excess my Mac tool bar to exit full screen mode when using the ubuntu VC anymore. So I Trashed the 10.10 and need to start again. What shall i do next time I reload or start another virtual machine with Maverick Meerhat? How do I upgrade to Natty Narwhal 11.04?



sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
[COLOR=#333333][FONT=UbuntuRegular]then update with[/FONT][/COLOR]

sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by coffeecat on 2014-05-30
In theory you could upgrade from 10.10 to 11.04 using the old-releases.ubuntu.com repository but 11.04 is long past end-of-life. As is the next 11.10. If you are going to create a new virtual machine you'd be better doing so with the still supported 12.04 (or rather use the newest 12.04.4 point release image) or the latest 14.04 LTS.

---

