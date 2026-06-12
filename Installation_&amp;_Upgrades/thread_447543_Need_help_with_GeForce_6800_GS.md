---
title: "Need help with GeForce 6800 GS"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by tb87670 on 2007-05-18
I just got Ubuntu, and its my first Linux system so I am pretty new. Main reason I chose Ubuntu was because I heard of the great community, so I hope someone will help.

 I need to know the necessary steps to install a GeForce 6800 GS video card onto my computer in Ubuntu Feisty 7.04. Please make them as simple as possible, and thanks in advance :)

---

### Post by vikramsharma on 2007-05-18
> **tb87670 said:**
> I just got Ubuntu, and its my first Linux system so I am pretty new. Main reason I chose Ubuntu was because I heard of the great community, so I hope someone will help.

 I need to know the necessary steps to install a GeForce 6800 GS video card onto my computer in Ubuntu Feisty 7.04. Please make them as simple as possible, and thanks in advance :)

I hope you have X up and running, go to System->Administration->Restricted Drivers Manager.  This app would automatically install drivers  for you.  

This part can get a little convoluted so please bear with me (you would require high speed Internet access for this), if the previous method fails you can go to the Synaptic Package Manager which can be found in System->Administration->Synaptic Package Manager go to the in the Settings menu go to the Repositories section. Under the Ubuntu software tab tick all the options and change the "Down from" "Server for United States" to "Main Server", you can also go to the updates section and check all the options there.  In the Synaptic Package Manager look for "nvidia-glx" and "nvidia-glx-dev" choose both and install.

Please reply incase you have any further queries.

---

### Post by tb87670 on 2007-05-18
Thanks a lot vikramsharma! Quick response in less than an hour. Only problem is now I feel stoopud:lolflag: Oh well now my video card works so I'm HAPPY!!

---

### Post by vikramsharma on 2007-05-18
> **tb87670 said:**
> Thanks a lot vikramsharma! Quick response in less than an hour. Only problem is now I feel stoopud:lolflag: Oh well now my video card works so I'm HAPPY!!

I am glad I could help you out.

---

