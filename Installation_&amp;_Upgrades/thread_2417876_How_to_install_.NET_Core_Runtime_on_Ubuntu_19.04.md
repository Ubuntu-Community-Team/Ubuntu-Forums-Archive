---
title: "How to install .NET Core Runtime on Ubuntu 19.04"
date: 2019-04-28
forum: Installation &amp; Upgrades
---

### Post by eshkol on 2019-04-28
Hi, I have trouble installing .NET Core Runtime on Ubuntu 19.04. I followed the instructions for Ubuntu 18.10 ([https://dotnet.microsoft.com/download/linux-package-manager/ubuntu18-10/runtime-current](https://dotnet.microsoft.com/download/linux-package-manager/ubuntu18-10/runtime-current)) with a slight change in the first command (replaced [FONT=courier new]18.10[/FONT] with [FONT=courier new]19.04[/FONT], see below).
However, neither package [FONT=courier new]aspnetcore-runtime-2.2[/FONT] nor [FONT=courier new]dotnetruntime-2.2[/FONT] are found in the last step. Also, no packages matching regex [FONT=courier new]aspnetcore-runtime*[/FONT] or [FONT=courier new]dotnet-runtime*[/FONT] are found.

Is there any way to get .NET Core Runtime functioning on Ubuntu 19.04 at this point?

Many thanks for any help!

The code:[COLOR=#000000]
[FONT=courier new]
[/FONT][/COLOR][FONT=courier new][COLOR=#000000]wget -q [/COLOR][[COLOR=#000000]https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb[/COLOR]]("https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb")
[COLOR=#000000]sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-2.2


[/COLOR][/FONT][COLOR=#FFFFFF][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by Guy_Rouillier on 2019-07-24
The included link now has instructions for 19.04, and I can verify they work.

My purpose for posting is to warn any one who happens upon this post *not* to use snaps to install dotnet.  [URL="https://snapcraft.io/dotnet-sdk"]https://snapcraft.io/dotnet-sdk
[/URL]
I've spent considerable time trying to get basic (auto-generated) dotnet apps working, with limited success.  The generated Console app works, but the generated GTK app does not.  I asked around a bit, and got responses like "a snap-based installation for dotnet is not supported, and will introduce significant issues."  Well, I can attest to that. :)

---

