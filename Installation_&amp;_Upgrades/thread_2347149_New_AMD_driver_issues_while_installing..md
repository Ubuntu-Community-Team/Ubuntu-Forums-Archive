---
title: "New AMD driver issues while installing."
date: 2016-12-22
forum: Installation &amp; Upgrades
---

### Post by jessedavid4 on 2016-12-22
So usually I ask friends about this, but it seems I am having issues. Actually, I've been having issues both with AMD and Nvidia driver installations.
But I just bought a new AMD card and want to use the new drivers and it seems I just run into the same issue.

Quoting from the AMD driver instructions download/install page.

[COLOR=#000000][FONT=Calibri][U]" Install
[/U]Once the archive is expanded on the local machine, run the included script (amdgpu-pro-install) to install the graphics stack.  During the installation you will be required to provide sudo access, and also to provide two confirmations to:[/FONT][/COLOR]

[LIST=1]
[*]Install the packages, and
[*]Allow installation of "unverified" packages from the AMDGPU-PRO archive.
[/LIST]
[COLOR=#000000][FONT=Calibri]
The script will use the package manager to install the components of the graphics stack, with a short delay during the DKMS (Dynamic Kernel Module Support) installation. From the directory where you extracted the archive, issue the following command:

cd amdgpu-pro-16.50-362463

./amdgpu-pro-install -y 

After this you can restart your machine to launch using the new graphics stack. "

So, after I download and extract. It seems I run into like an issue that makes absolutely no sense.

IT DOES NOT LET ME RUN THE INSTALLATION SCRIPT.

I will run it, run in terminal and it will open terminal for maybe .2 of a second and it will close it.
Then nothing happens. I ran it in display and gave me some useless information.

I've tried to wget it, and install it and it will not work:

 wget [https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-16.50-362463.tar.xz](https://www2.ati.com/drivers/linux/ubuntu/amdgpu-pro-16.50-362463.tar.xz)

- It'll just say incomplete and send the files to a file download link application.

I've tried to reinstall it like 10 times, extract, and run the script -- Nothing works.

This same issue like came up with Nvidia and I am starting to wonder the issue is coming from somewhere else.

Idk... I can't see my taskbar because cinnamon crashes every time I log in. (this is before I have my drivers) And so I cannot get to system setting and adjust anything. So I am really lost here and this is why I only jump on linux like once a month now, because I can't seem to get anything to work.

Any help would be appreciated. And I bet this information is likely not helpful, so a request for more information will be given immediately to help me resolve my issue(s)!
-Jesse[/FONT][/COLOR]

---

### Post by QIII on 2016-12-22
Hello!

Which release of Ubuntu are you running and what is the model of your AMD card?

---

