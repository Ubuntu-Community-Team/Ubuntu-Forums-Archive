---
title: "No internet connection when connect to OpenVPN"
date: 2018-05-26
forum: Installation &amp; Upgrades
---

### Post by mac187 on 2018-05-26
I followed this tutorial -> [https://nordvpn.com/tutorials/linux/openvpn/](https://nordvpn.com/tutorials/linux/openvpn/) for how to acsess trough shell.

It working with password and everything but when i try to visit pages i dont have connection ? But when i cancel with Ctrl + C then my internet works again..

Anythign i can do to make it works ? i want to use shell..

Im using Ubuntu 18.04

Thanks for all help

---

### Post by Skaperen on 2018-05-27
when you cancel with Ctrl+C. it intercepts the SIGINT signal and restores the original routing before it exits (the right thing to do).

i have used ssh for a VPN before (not with OpenVPN or NordVPN) so i know it can be done.  however, most people never have done it this way.  probably the biggest reason is that it is recommended against.  there are good reasons for this general recommendation.  how it will affect you is that few people will be able to help you.  so what i recommend is to take the approach most people do and set up OpenVPN for direct UDP access.  i assume NordVPN allows this.  if not, then i would suggest choosing another VPN provider.  UDP is the way to go. OpenVPN does the encryption and decryption.  you don't need ssh to make this secure.

i made my own VPN for "free" on the server i already leased to host my websites, my DNS, and various other thing (it runs Ubuntu 16.04 LTS just as i do on my laptop at home).  i am also brainstorming a script to set it up and run it on an AWS cloud instance under the free tier (will initially require Ubuntu on your end, too).  it will include IPv6.  but it's not ready, yet.

---

