---
title: "Back from 16.04 to 14.04"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by philo4 on 2016-08-08
Hi everyone, 
Since upgrading from 14.04 to 16.04 LTS about 4 days ago, my laptop does not work.  What to do to go back to 14.04?
Thanks for your help
Phil

---

### Post by PaulW2U on 2016-08-08
> **philo4 said:**
> Since upgrading from 14.04 to 16.04 LTS about 4 days ago, my laptop does not work.  What to do to go back to 14.04?
philo4, there is no official **downgrade** path after an **upgrade**.

[How to roll back Ubuntu to a previous version?]("http://askubuntu.com/questions/49869/how-to-roll-back-ubuntu-to-a-previous-version") is a lengthy article that has been posted on Ask Ubuntu but there are numerous warnings that advise of a lengthy process, that the upgrade process is "one way" and that the resulting installation may not be what you started out with.

You really need to reinstall 14.04 or try to resolve whatever problems you are having with 16.04.

---

### Post by mörgæs on 2016-08-08
Yes, reinstall 14.04 is the way to go if you want this release, but before you abandon 16.04 I suggest that you try a fresh install of this one, too.

---

### Post by philo4 on 2016-08-11
Hi PaulW2U and Moergaes (Sorry, there is no umlaut with this qwerty version!),
Many thanks for your replies which suggest it is better to move on with the installation of 16.04.
In that case, please explain to me what steps I do have to take now.
Regards

---

### Post by mörgæs on 2016-08-11
Next step is finding a guide describing how to create a bootable USB stick. There are many good ones around.

---

### Post by PaulW2U on 2016-08-11
> **philo4 said:**
> Many thanks for your replies which suggest it is better to move on with the installation of 16.04.
In that case, please explain to me what steps I do have to take now.
Upgrading from one LTS to another can be troublesome. Although the process is tested I'm sure it is not tested enough as there are hundreds of packages that need to be upgraded and we all have different software installed on of course a very wide range of hardware.

You now have to decide whether to go back to 14.04, an installation you'll still need to upgrade in due course, try to resolve your problems on your existing 16.04 installation or start again with a new 16.04 installation. I'd go for the third option myself. But try 16.04 in a live session first to make sure everything works as it should.

See [How to create a bootable USB stick on Ubuntu]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu") to try out Ubuntu 16.04.

---

### Post by philo4 on 2016-08-12
Which guide would you recommend me to use, in order to create a bootable USB stick?

---

### Post by philo4 on 2016-08-12
Hi PaulW2U,
The solution is probably to go for a new 16.04 installation. I checked the link you provided ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)). This only seems possible when one still has access to a working computer with Linux/Ubuntu, which is not my case for the moment. Any other suggestion?
In the meantime, the Recovery Menu (filesystem state: read-only) leads to:

Ubuntu 16.04.1 LTS philo-laptop tty1

philo-laptop login: philo
Password:
Last login: Fri Aug 12 14:04:41 GMT 2016 on tty1
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 3.13.0-92-generic i686)

* Documentation:   [https://help.ubuntu.com](https://help.ubuntu.com)
* Management:      [https://landscape.canonical.com](https://landscape.canonical.com)
* Support:             [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
philo@philo-laptop:~$


Could that help with moving forward?  Is there any command to come out of that terminal towards the dash (with all applications)?

---

### Post by PaulW2U on 2016-08-12
> **philo4 said:**
> Since upgrading from 14.04 to 16.04 LTS about 4 days ago, my laptop does not work.
You say that your laptop does not work but what actually is not working? Your last post quoted some screen output which clearly shows that it is working although obviously not fully.
> **philo4 said:**
> This only seems possible when one still has access to a working computer with Linux/Ubuntu, which is not my case for the moment. Any other suggestion?
Do you have another computer or laptop that is running Windows?

[How to create a bootable USB stick on Windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") might be of help.

How did you install 14.04 on your laptop? Can you not use the same method to install 16.04?

---

### Post by grahammechanical on 2016-08-12
If you are getting to a recovery menu then select Resume. What happens then. Actually, Resume is the way out of the recovery menu unless we power off or run a shutdown command from Root shell prompt.

But you only asked about going back to 14.04.

Regards.

---

### Post by philo4 on 2016-08-16
Hi grahammechanical,

If 16.04 would work on my laptop, fantastic!  If 14.04 works on my laptop, fantastic. 

Further to your question, the Recovery Menu (filesystem state: read-only) leads to:

 Ubuntu 16.04.1 LTS philo-laptop tty1

 philo-laptop login: philo
 Password:
 Last login: Fri Aug 12 14:04:41 GMT 2016 on tty1
 Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 3.13.0-92-generic i686)

 * Documentation:   [[COLOR=#dd4814]https://help.ubuntu.com[/COLOR]]("https://help.ubuntu.com/")
 * Management:      [[COLOR=#dd4814]https://landscape.canonical.com[/COLOR]]("https://landscape.canonical.com/")
 * Support:             [[COLOR=#dd4814]https://ubuntu.com/advantage[/COLOR]]("https://ubuntu.com/advantage")
 [EMAIL="philo@philo-laptop:~$"]philo@philo-laptop:~$[/EMAIL]

---

### Post by philo4 on 2016-08-16
One question though:
Is what is commonly named as [[COLOR=#dd4814]a bootable Live USB [/COLOR]]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")a simple saving of the downloadable file (found for instance at [http://old-releases.ubuntu.com/releases/14.04.2/](http://old-releases.ubuntu.com/releases/14.04.2/)) on a USB key, or is there anything else to be done?

---

### Post by philo4 on 2016-08-20
Dear PaulW2U, Moergaes and Grahammechanical,
Your contributions have been highly appreciated.  Suddenly, it gave a sense of one not being left on one's own in a technological island. 
As the computer has refused so far to boot on the Live USB, CDROM, Boot Repair Kit,..., hopefully I will come across in person with a Linux user for whom this challenge will be a simple game.
Once again, many thanks ! 
Philo

---

### Post by mörgæs on 2016-08-22
If you get in touch with a local Linux user group chances are good that someone will take a look.

---

