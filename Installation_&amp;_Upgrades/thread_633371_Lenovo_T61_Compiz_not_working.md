---
title: "Lenovo T61 Compiz not working"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by digyourownhole on 2007-12-06
Yesterday I installed Ubuntu 7.10 on a Lenovo Thinkpad T61 T7500.

When I go to System > Preferences > Appearance, than to Visual Effects, when I select Extra, i get this message: "Desktop effects could not be enabled".

Browsing this forum I came across this site: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61#Accelerated_Video_and_Desktop_Effects](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Release_Candidate_on_a_ThinkPad_T61#Accelerated_Video_and_Desktop_Effects)

There they claim that Visual Effects should work. However it does not. The site says "to enable accelerated 3D support click System->Administration->Restricted Drivers Manager".
However, selecting that, i get the message: "Your hardware does not need any restricted drivers." and I cannot do anything.

The site says the following about that: "If the Restricted Drivers Manager fails to install the driver you can use the Envy tool from: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html). This tool is unsupported and the only supported method of installing the Nvidia drivers is via Synaptics and the Restricted Drivers Manager".

Envy installed allright. But still i am unable to Select Extra in System > Preferences > Appearance, than to Visual Effects.

Anybody?

---

### Post by FilmAficionado on 2008-02-04
If you have integrated Intel graphics, what you need to do is:

COMPIZ:

sudo gedit /usr/bin/compiz

T=&#8221;$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12&#8243; # intel 965
(comment out):
#T=&#8221;$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12&#8243; # intel 965

NOW, compiz starts working with that but then there are problems. Supposedly video cannot work (I can confirm I can't get a DVD to play in VLC). Some effects don't work, REFLECTIONS still do not work, nor does the negative filter. I don't get it. So many problems with this now...

---

