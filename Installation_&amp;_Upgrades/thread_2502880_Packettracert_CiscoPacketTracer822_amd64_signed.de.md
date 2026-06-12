---
title: "Packettracert CiscoPacketTracer822_amd64_signed.deb  packet  fix on ubuntu 4.04.1 LTS"
date: 2024-12-04
forum: Installation &amp; Upgrades
---

### Post by matosborges39 on 2024-12-04
Add this repository
You should be able to use any of the listed mirrors by adding a line to your /etc/apt/sources.list like this:


deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) jammy-updates main universe
Replacing cz.archive.ubuntu.com/ubuntu with the mirror in question.


atualizar pacotes comando sudo apt-get update && apt-get upgrade.


install packettracert comand dpkg -i CiscoPacketTracer822_amd64_signed.deb 


this fixed the broken packets in the packetracert 822_amd64_signed.deb installation

---

