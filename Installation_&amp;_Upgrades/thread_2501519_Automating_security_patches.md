---
title: "Automating security patches"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by tvining on 2024-10-11
I have about 200 hosts that I need to run security patches on weekly.
A few things to keep in mind:

1.  I cannot install anything into the windows environment, but I have basic tools (putty, plink, powershell, etc)
2.  I cannot add anything to the linux environment (it's a stripped kernel with VERY specific options)
3.  I must ALWAYS answer no to any prompt (update boot options, allow Wireshark for non-sudo, etc)
4.  I must (obviously) always answer YES to downloading the required updates and allowing the disk space.
5.  I am NOT afraid to send the password plain text, (I would include a clear history command when done) but I could be open to installing a key pair to make things smoother.
6.  About every 3-4 months, we get a complete new release of linux to load, so anything I put on the linux machine (keys, accounts, etc) are wiped clean, and I have to re-add them.  No way to build them into the vendor's release.
7.  I can't CRON the updates, because occasionally the updates break the machines.  (replace files that the client software relies on).   I normally test a few machines on Monday, then run all the updates Tuesday.  Can't wake up to 200 broken machines that need to be reimaged.  :-D

Right now, I have an excel list of IP's and I concatenate ("ssh <login>@",ip) and manually copy and paste that to powershell, use a macro keyboard to send sudo, password, "apt update; apt upgrade; exit" and then answer the prompts, type exit and move on to the next.  Would like to make it more autonomous so I can drink my coffee.

---

### Post by ActionParsnip on 2024-10-11
Try Ansible. You can run updates across all your servers using one playbook. Dead simple. Just install ansible on a systems, generate an SSH keypair and put the public key in the root keystore. You can then run commands as root from the server.
Dead simple. You can also make other playbooks to do other tasks. With 200 servers, this will make your life a LOT easier.

---

### Post by tvining on 2024-10-11
> **ActionParsnip said:**
>  Just install ansible on a systems, generate an SSH keypair and put the public key in the root keystore. 

Refer to my guideline number 1.   I can't install anything on the Windows environment, nor add to the linux environment.  I'd love to use ansible, but it's not in the cards.

---

### Post by ActionParsnip on 2024-10-11
> **tvining said:**
> Refer to my guideline number 1.   I can't install anything on the Windows environment, nor add to the linux environment.  I'd love to use ansible, but it's not in the cards.

Ah. Apologies. You could make a bastardized Ansible in BASH. You can configure certain commands in sudo for a specific username to not need a password or use expect to pass the sudo password as needed.
You could have BASH loops going through lists of servers copying data where it's needed, or to a temporary storage to then move in place with another loop. Messy but possible. 

Ansible doesn't need to be a Web GUI all guns blazing. You just need the Ansible package installing on a system and you can use it as you expect in command line. It's a simple enough creature. Only gets complex if you start syncing inventories from Satellite etc. 

I'm guessing this is in industry, I'd really make a case for Ansible. It'll save you a tonne of time.

---

