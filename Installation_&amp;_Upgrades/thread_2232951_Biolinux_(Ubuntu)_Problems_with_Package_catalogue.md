---
title: "Biolinux (Ubuntu): Problems with Package catalogue"
date: 2014-07-05
forum: Installation &amp; Upgrades
---

### Post by Katzwinkel on 2014-07-05
I wanted to install an external module for python a few days ago (Twilio) but ran into problems with the oracle java7 requirement (was not installed and could not be installed). Ever since I now have problems installing anything. I keep geting the following message:

"biolinux Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now?"

But wen I click "OK" it always aborts the repair process with the message "Package operation failed" (however It won't let me look into the details).

When I look into the Software-Center history it seems that each time it tries to "repair the catalogue" it is actually trying to install "Oracle-Java8-installer" but fails every time. In fact, right now I am trying to install the newest version of R-Studio at the moment (the last version worked just fine), and the problem remains.

what can I do?

---

### Post by frogotronic on 2014-07-06
You should send an eMAIL to the BioLinux support listserv:  [email]bio-linux@nebclists.nerc.ac.uk[/email]

---

### Post by Katzwinkel on 2014-07-06
Thanks,
I've written to the mailing list. However since Biopython is based on Ubuntu, I was wondering if this might not just be a general Linux problem (not specific for Biolinux).

Principally there seems to be a problem with instaling oracle-java8. somehow the packaga catalogue can't deal with the fact that this installation failed and wants to keep installing it before allowing anython else. I#ve tried some other fixes I found (running "sudo apt-get update" followed by "sudo apt-get -f install") but then it seems to want to finalize the oracle-java8 installation by removing some other installed packages.

I am now a bit afraid that this might not be such a good Idea (I mean theres probably a reason open-jdk is generally used rather than oracle-java) and I#m wondering if i cannot just somehow tell the system to stop trying to install oracle-java alltogether.

How would I do that?

---

### Post by Vladlenin5000 on 2014-07-07
> **Katzwinkel said:**
> I#ve tried some other fixes I found (running "sudo apt-get update" followed by "sudo apt-get -f install") but then it seems to want to finalize the oracle-java8 installation by removing some other installed packages.

Yes, that's exactly what it's supposed to do. The "-f" argument AKA "--fix-broken" is intended to replace broken packages.


> I am now a bit afraid that this might not be such a good Idea (I mean  theres probably a reason open-jdk is generally used rather than  oracle-java) and I#m wondering if i cannot just somehow tell the system  to stop trying to install oracle-java alltogether.

Besides one being open source and the other proprietary there's no other compelling reason to use open-jdk instead of Oracle's. Open-jdk works for almost everything the other works but there's the odd software out there that specifically requires the proprietary one. You just stumbled in one of those.


> How would I do that?

Unlike with the previous questions this hasn't an easy answer. It depends on how you tried to install Oracle's in the first place.

---

