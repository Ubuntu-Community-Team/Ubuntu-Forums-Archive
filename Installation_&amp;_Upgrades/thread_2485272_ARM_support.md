---
title: "ARM support"
date: 2023-03-24
forum: Installation &amp; Upgrades
---

### Post by deepbeige on 2023-03-24
[COLOR=#232629][FONT=-apple-system]I've not been able to reliably find good solid information on installs that support Annapurna Labs ARM CPUs. I know it ubuntu will install on Marvell ARM CPUs. 

the hardware is a QNAP NAS that has the[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system] Annapurna Labs ARM CPU I've talked about. 

any help?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-03-25
What model with which CPU?

And please link to your other threads. I think I see at least one at AskUbuntu... Is this your? [https://askubuntu.com/questions/1460679/ubuntu-server-install-on-annapurna-labs-cpu](https://askubuntu.com/questions/1460679/ubuntu-server-install-on-annapurna-labs-cpu)

---

### Post by deepbeige on 2023-03-25
[SIZE=3]yah that's my post. - I was not thinking about linking the two, that's' on me. 

to answer your question. 

ts-832px with [COLOR=#333333][FONT=Roboto]AL324 ARM® Cortex-A57[/FONT][/COLOR][/SIZE]

---

### Post by MAFoElffen on 2023-03-26
From what I see, I don't think natively. 

QNAP is a different animal... It uses it's own OS, which is QTS.  and says it has an Integrate Linux... But in it's implementation of, is really an LXC container. It says that "Ubuntu" is an option, but is installed from their QTS App Store as "Ubuntu Station". [https://www.qnap.com/solution/linux-station-app/en/](https://www.qnap.com/solution/linux-station-app/en/)

I do not see where anyone has tried to install Ubuntu to a QNAP NAS device anywhere, as installing in as a traditional physical OS. 

I know that  have run the Ubuntu Server arm64 [I]ISO on KVM guests set up with Cortex-A57 CPU's... But physically, the device would have to be able to boot from USB... Can your NAS boot from USB?

If so, I can point you to an ISO image of the Arm64 Ubuntu Server Edition 22.04, and give you instructions of how to test drive it as a Live Image.
[/I]

---

