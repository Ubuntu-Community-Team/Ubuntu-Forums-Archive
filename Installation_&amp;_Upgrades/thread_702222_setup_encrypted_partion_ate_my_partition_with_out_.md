---
title: "setup encrypted partion ate my partition with out warning."
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by jimlay on 2008-02-20
I installed ubuntu 7.10 (32bit) alt with an encrypted root about 2 weeks ago and got everything working. I upgraded my ram and decided I wanted to try amd64. I chose to install the 64bit on a separate hard drive but I wanted to mount the encrypted partition in the new system.

In the installer I selected my encrypted partition (with type unknown) and selected "use as encrypted device". Then I selected the "configure encrypted partitions" up at the top and carefully read the message. It said after I'd mounted the encrypted volumes I wasn't going to make any more changes to the underlying partition table.

What it didn't tell me was that it was about to run luksFormat on the root partition of my other ubuntu install. Assuming I was performing a reversible action I hit ok and tried to setup my existing xfs partition. At this point the gui only offered the option to format the partition and I didn't want to do that. I backed out and canceled the install but the damage had already been done.

The screen in the alt install that explains "you are about to mount your encrypted volume" needs to mention that if there is data there, especially an encrypted volume already, you are destroying it.

I've just lost about 60gb of data. I had everything important backed up, but I'm still a little bit pissed.

How do I ensure that the language gets an update? Should I file a bug?

Josie

---

