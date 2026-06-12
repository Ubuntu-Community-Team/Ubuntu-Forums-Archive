---
title: "Create a custuom baremetal image for ubuntu 22.04"
date: 2022-11-29
forum: Installation &amp; Upgrades
---

### Post by unixadmn on 2022-11-29
Hello Folks,

I have a request to create a baremetal image for multiple BM deployments, I'm looking for the help from the experts for the process and tool to do it.
To be more specific it should be just like a VMWare template to deploy new VM's.

Appreciate all your time and help in advance.

Thanks,
Sri

---

### Post by ActionParsnip on 2022-12-01
I'd boot to live USB desktop and mount an external drive. Make an ISO of the boot drive (I assume you made this small to make this easier) using dd. You can then dd to another drive and get the same config.
You could also use chef / puppet / ansible instead and have servers get their configuration centrally and you can manage configurations easily.

---

### Post by unixadmn on 2022-12-06
Thanks [**[COLOR=#DD4814][B]ActionParsnip**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1079078") for the response 
I was planning to use [https://www.linuxhelp.com/how-to-install-mondo-rescue-disaster-recovery-tool-in-linux](https://www.linuxhelp.com/how-to-install-mondo-rescue-disaster-recovery-tool-in-linux)

---

