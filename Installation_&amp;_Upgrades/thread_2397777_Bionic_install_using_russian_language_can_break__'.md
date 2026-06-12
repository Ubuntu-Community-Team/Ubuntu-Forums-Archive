---
title: "Bionic install using russian language can break  'apt update'"
date: 2018-08-03
forum: Installation &amp; Upgrades
---

### Post by jazzbiker on 2018-08-03
Hi!
Not so far ago I've installed Bionic on a laptop and faced the problem during 'sudo apt update':
```

[COLOR=#333333][FONT=&amp]&#1055;&#1086;&#1083;:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
&#1057;&#1091;&#1097;:2 http://archive.canonical.com/ubuntu bionic InRelease
&#1054;&#1096;&#1082;:3 http://ru.archive.ubuntu.com/ubuntu bionic InRelease
  &#1042;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1072;&#1103; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1087;&#1086;&#1087;&#1099;&#1090;&#1082;&#1077; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; IP-&#1072;&#1076;&#1088;&#1077;&#1089; «ru.archive.ubuntu.com»
&#1054;&#1096;&#1082;:4 http://ru.archive.ubuntu.com/ubuntu bionic-updates InRelease
  &#1042;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1072;&#1103; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1087;&#1086;&#1087;&#1099;&#1090;&#1082;&#1077; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; IP-&#1072;&#1076;&#1088;&#1077;&#1089; «ru.archive.ubuntu.com»
&#1054;&#1096;&#1082;:5 http://ru.archive.ubuntu.com/ubuntu bionic-backports InRelease
  &#1042;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1072;&#1103; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1087;&#1086;&#1087;&#1099;&#1090;&#1082;&#1077; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1090;&#1100; IP-&#1072;&#1076;&#1088;&#1077;&#1089; «ru.archive.ubuntu.com»
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086; 83,2 kB &#1079;&#1072; 2&#1089; (43,5 kB/s)
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;…
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;…
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;…
&#1042;&#1089;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1080;&#1084;&#1077;&#1102;&#1090; &#1087;&#1086;&#1089;&#1083;&#1077;&#1076;&#1085;&#1080;&#1077; &#1074;&#1077;&#1088;&#1089;&#1080;&#1080;.


[/FONT][/COLOR]

```

As I found out, the problem appears after installing Lubuntu in russian language. Update servers were set to "Server of Russian Federation". Authorities of some countries (in my case Ukraine) deny access to net resources of Rus.Fed.
I changed update servers to "Main server" using synaptic, and everything goes right.
Maybe it is possible to ask developers of system installation not to put servers form Rus.Fed into 'sources.list', because this may cause problems?
Ubuntu is so well suited to be the first Linux, but this issue may be trouble for newbies.

---

