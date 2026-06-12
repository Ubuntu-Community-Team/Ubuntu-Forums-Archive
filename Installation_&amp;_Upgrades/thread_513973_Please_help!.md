---
title: "Please help!"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by gallonero on 2007-07-31
Hi! i'm new in the community and in linux. i have a problem and i don't know how to solve it. when i install a program (add/remove programs) an error message is shown and says...

E: clvm: &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 3
E: redhat-cluster-suite: &#960;&#961;&#959;&#946;&#955;&#942;&#956;&#945;&#964;&#945; &#949;&#958;&#940;&#961;&#964;&#951;&#963;&#951;&#962; - &#945;&#966;&#942;&#957;&#949;&#964;&#945;&#953; &#956;&#951; &#961;&#965;&#952;&#956;&#953;&#963;&#956;&#941;&#957;&#959;
E: system-config-cluster: &#960;&#961;&#959;&#946;&#955;&#942;&#956;&#945;&#964;&#945; &#949;&#958;&#940;&#961;&#964;&#951;&#963;&#951;&#962; - &#945;&#966;&#942;&#957;&#949;&#964;&#945;&#953; &#956;&#951; &#961;&#965;&#952;&#956;&#953;&#963;&#956;&#941;&#957;&#959;

i use the greek version of ubuntu 7.04... The message says that...

[B]E: clvm: the subprossedure post-installation script has returned in error state 3
E: redhat-cluster-suite: problems of dependence - is left not regulated
E: system-config-cluster: problems of dependence - is left not regulated
[/B]

is this serious???

Thanks for the help!!!

---

### Post by wpshooter on 2007-07-31
Sounds perhaps like a problem with your repository listing.

Go into software sources and make sure that all available repositories are marked including universe and multi-universe and then exit out of the window and reload when it prompts you.

I would then restart the computer and then give your opeation another try.

Good luck.

---

