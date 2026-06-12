---
title: "can't find lib32asound2 in 13.10 64-bit"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by nomenunknown on 2013-10-18
I just fresh installed 13.10, but now the teamviewer.deb file won't install due to an unresolvable dependency: lib32asound2. Wine 1.4 is already installed. Where can I find that package for 13.10? Also, no Steam yet for 13.10? Is it just me? Thanks all!

---

### Post by rihikz on 2013-10-18
Steam and team viewer should work perfectly fine.
Are you using the correct architecture?

---

### Post by nomenunknown on 2013-10-18
Yes. I installed 13.10 desktop 64-bit. When I open Software Center, Steam says "already puchased" and "Steam not yet available for this version of Ubuntu".

When I open teamviewer.deb64 in Software Center, the error says "unresolvable dependency lib32asound2". This package does not show up in Synaptic Package Manager.

---

### Post by heir4c on 2013-10-18
The package is deleted from saucy: [https://launchpad.net/ubuntu/saucy/amd64/lib32asound2](https://launchpad.net/ubuntu/saucy/amd64/lib32asound2)
You can download it from: [https://launchpad.net/ubuntu/saucy/amd64/lib32asound2/1.0.25-4ubuntu4](https://launchpad.net/ubuntu/saucy/amd64/lib32asound2/1.0.25-4ubuntu4)
Direct link for download: [http://launchpadlibrarian.net/139194357/lib32asound2_1.0.25-4ubuntu4_amd64.deb](http://launchpadlibrarian.net/139194357/lib32asound2_1.0.25-4ubuntu4_amd64.deb)

---

### Post by nomenunknown on 2013-10-18
Thank you, that was very helpful! I did hit one roadblock though: when I tried to install the older version of libasound2, both Synaptic and Software Center told me I couldn't because a newer version is installed. Also, the "Force Version" option in Synaptic was greyed out. What can I do about that?

---

### Post by heir4c on 2013-10-18
Look in the link below and than answer #3. He used the 64bit what give a error. But in the second link he post there he installed a different package (MultiArch) and than it solved the problem (I think it is the 32 bit version. I try it here and no (red) error (I Installed it with gdebi).
[https://answers.launchpad.net/ubuntu/+question/234339](https://answers.launchpad.net/ubuntu/+question/234339)
(I think: teamviewer 64bit is not ready for the new Ubuntu.)

---

### Post by nomenunknown on 2013-10-18
Ah, I think you're right. In the meantime, I've emailed Teamviewer support about it, so we'll see what happens. Thanks very much for your assistance!

---

### Post by heir4c on 2013-10-19
Done with pleasure!
You installed now the other .deb and it works?

---

### Post by demontager on 2013-10-19
Got same dependency error lib32asound2 when trying to install Teamviewer amd64 on Lubuntu 13.10 64bit. For now i'm using .tar.gz version of teamviewer, works fine but lack of autostart feature.
[URL="http://ubuntuforums.org/member.php?u=1872153"][B][COLOR=#000000]
nomenunknown[/COLOR][/B][/URL],  Please, let us know regarding their reply. I'll do e-mail myself as well.

UPDATE: Sent email to support. Actual dependency error screen [http://simplest-image-hosting.net/png-0-team1](http://simplest-image-hosting.net/png-0-team1)

---

### Post by nomenunknown on 2013-10-19
Ok. So now on the Teamviewer website, there is a link by the 64-bit version that, long-story-short, says just install the 32-bit version. I haven't received an email back yet, but I did find that. Indicidentally, I did install the 32-bit version and it works. Maybe I'm being a little OCD, but I'd really rather have the 64-bit version!

---

### Post by demontager on 2013-10-20
Yes, also tried multiarch deb and it works. They haven't reply to my email as well

---

### Post by franc000182 on 2013-10-22
> **demontager said:**
> Yes, also tried multiarch deb and it works. They haven't reply to my email as well

Multiarch .deb also worked for me. Anyway it's a 32bit application running a custom wine version

---

### Post by lucasfxd on 2013-10-25
I'm using Ubuntu 13.10, tried to install the last team viewer x64 package and had this problem.
I downloaded and tried to install "lib32asound2_1.0.25-4ubuntu4_amd64.deb", and I got this message: Dependency is not satisfiable: libasound2 (= 1.0.25-4ubuntu4).
And then, when I tried to install "libasound2_1.0.25-4ubuntu4_amd64.deb", it says: "a later version is already installed."
When I tried to remove my current libasound2, it says it will remove a lot of programs, including Firefox... WTF.........

---

### Post by jonathan-l-harrison on 2013-10-30
I am trying to resolve an IPT issue, and getting help from China who have suggested using this app.  I had the same issues trying to install it.  Not fun.  I too have just updated to 13:10 on a 64-bit machine.

---

### Post by mauriziodepitta on 2013-12-05
I agree with heir4c.
I just got the same problem after a messed-up update.
I tried to fix unmet dependencies and missing libraries requested to install Teamviewer i68, with no success. Yet installing the Multiarch version solved the problem apparently.

---

### Post by heir4c on 2013-12-07
> **nomenunknown said:**
> Ok. So now on the Teamviewer website, there is a link by the 64-bit version that, long-story-short, says just install the 32-bit version. I haven't received an email back yet, but I did find that. Indicidentally, I did install the 32-bit version and it works. Maybe I'm being a little OCD, but I'd really rather have the 64-bit version!

All 32bit programs must work on the 64bit architecture. If it works, then that's fine, no? 
You can't install the 64bit version because the ia32-libs package on Ubuntu and Debian system is no more in the repo's.
On the website of Teamviewer there give also info about that: [http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch](http://www.teamviewer.com/en/help/363-How-do-I-install-TeamViewer-on-my-Linux-distribution.aspx#multiarch)
And here also a link to a Q&A of Askubuntu: [http://askubuntu.com/questions/362951/install-teamviewer-using-a-64-bits-system-but-i-get-lib32asound2-dependency-erro](http://askubuntu.com/questions/362951/install-teamviewer-using-a-64-bits-system-but-i-get-lib32asound2-dependency-erro)

---

