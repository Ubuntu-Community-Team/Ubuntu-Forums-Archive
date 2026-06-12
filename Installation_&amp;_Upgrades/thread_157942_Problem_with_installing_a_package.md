---
title: "Problem with installing a package"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by technokiran on 2006-04-10
Haiii, I was trying to share internet by following one thread posted in this forum
              [http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)
and when i tried to install dnsmasq by giving commands the reply is
                         #apt-get install dnsmasq
                  Reading pakage lists .... done
                  Building dependency tree ..... done
                  E:couldn´t find package dnsmasq
finally its giving the error couldnt find package but the system is connected to internet.
And i think it will install directly from the net and thereis no need of installing any packages. Can u help me this pleasee....
             I will be thankfull if u can help me out.....

---

### Post by Kapre on 2006-04-10
[QUOTE=technokiran]Haiii, I was trying to share internet by following one thread posted in this forum
              [http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)
and when i tried to install dnsmasq by giving commands the reply is
                         #apt-get install dnsmasq
                  Reading pakage lists .... done
                  Building dependency tree ..... done
                  E:couldn´t find package dnsmasq
finally its giving the error couldnt find package but the system is connected to internet.
And i think it will install directly from the net and thereis no need of installing any packages. Can u help me this pleasee....
             I will be thankfull if u can help me out.....[/QUOTE]

teknokiran - why dont you try using the Synaptic Package Manager? Point and click on the app you want to install. But if you really prefer the terminal, try doing "sudo apt-get update" (to make sure your repos are updated) then sudo apt-get install dnsmasq.

K

---

### Post by technokiran on 2006-04-11
haaa, Thanks for the reply, But even it doesn´t worked. When i had given command for database update also its giving error.
                  But i got it. Actually we have to enable the ¨universe¨ repository in /etc/apt/sources.list file, by default # will be present before them and we have to delete them. And then when i had give update database it had updated my database and know i am able to install any softwares.
         Any how thanks for ur reply, byeee.

---

