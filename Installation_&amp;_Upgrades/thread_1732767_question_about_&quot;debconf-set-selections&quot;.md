---
title: "question about &quot;debconf-set-selections&quot;"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by yuhanz on 2011-04-18
Hi all,

I am writing a .sh script to automate the installation process using debconf-set-selections. it passes most of the installation steps without asking questions. However, it still brings up a blue screen asking ok confirmation to restart some services for libpam0g.

Here are the debconf-set-selections parameters that I set (I got them by [FONT=monospace]"[/FONT]debconf-get-selections |grep ^libpam0g" from the terminal).


export DEBIAN_FRONTEND=noninteractive
export DEBIAN_PRIORITY=critical

sudo echo "libpam0g    libpam0g/restart-services    string    exim4 cron" | debconf-set-selections
sudo echo "libpam0g    libpam0g/xdm-needs-restart    error" | debconf-set-selections
sudo echo "libpam0g    libpam0g/restart-failed    error" | debconf-set-selections

DEBIAN_FRONTEND=noninteractive sudo apt-get update -f -y --force-yes --quiet --yes
DEBIAN_FRONTEND=noninteractive sudo apt-get upgrade -f -y --force-yes --quiet --yes


Is there anything missing? :confused:

Thank you.

---

### Post by yuhanz on 2011-04-18
hi all,

problem solved by:

sudo DEBIAN_FRONTEND=noninteractive apt-get update -f -y --force-yes --quiet --yes

 it was my mistake by putting "sudo" at the back.

DEBIAN_FRONTEND=noninteractive sudo apt-get update -f -y --force-yes --quiet --yes

thanks!

---

