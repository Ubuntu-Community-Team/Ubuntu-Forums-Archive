---
title: "I need help running the Windows Subsystem for Linux"
date: 2021-03-05
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2021-03-05
[FONT=&quot]I followed these instructions: "[/FONT][How to Run a Linux Desktop Using the Windows Subsystem for Linux]("https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/")[FONT=&quot]".[/FONT]
[FONT=&quot]But instead of installing the LXDE environment I chose Gnome. Other than that I did exactly as instructed.[/FONT]

[FONT=&quot]So towards the end of the page after running XLaunch, I am supposed to enter this command "[/FONT][COLOR=#000000][FONT=Consolas]startlxde[/FONT][/COLOR][FONT=&quot]", assuming I installed the LXDE environment. So what am I supposed to enter if I installed Gnome? startgnome did not work.[/FONT]

[FONT=&quot]Thanks guys[/FONT]

[FONT=open sans, sans-serif, Arial, Tahoma, Calibri, Geneva, sans-serif]JDL[/FONT]

---

### Post by yancek on 2021-03-06
You should be able to just type in:  startx

---

### Post by javierdl on 2021-03-06
> **yancek said:**
> You should be able to just type in:  startx

I tried it. It told me that that command was not found, but I could install "xinit", so I did.
When I used "startx" again after installing xinit, it replied this:

"```
 startx  xauth:  file /home/drpeppercan/.Xauthority does not exist   config/udev: failed to bind the udev monitor   [config] failed to pre-init udev  X.Org X Server 1.20.9  X Protocol Version 11, Revision 0   Build Operating System: Linux 4.15.0-130-generic x86_64 Ubuntu  Current Operating System: Linux DESKTOP-TKTALUL 4.4.0-19041-Microsoft #488-Microsoft Mon Sep 01 13:43:00 PST 2020 x86_64Kernel command line: BOOT_IMAGE=/kernel init=/init   Build Date: 17 January 2021  09:13:31AM                                                                                 xorg-server 2:1.20.9-2ubuntu1.2~20.04.1 (For technical support please see http://www.ubuntu.com/support)                Current version of pixman: 0.38.4  Before reporting problems, check http://wiki.x.org  to make sure that you have the latest version.  Markers: (--) probed, (**) from config file, (==) default setting,   (++) from command line, (!!) notice, (II) informational,  (WW) warning, (EE) error, (NI) not implemented, (??) unknown.  (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  6 07:12:48 2021                                                    (==) Using system config directory "/usr/share/X11/xorg.conf.d"  (EE)   Fatal server error:   (EE) xf86OpenConsole: Switching VT failed   (EE)  (EE)  Please consult the The X.Org Foundation support  at http://wiki.x.org  for help.   (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.  (EE)   (EE) Server terminated with error (1). Closing log file.  xinit: connection to X server lost   deallocvt: ioctl VT_DISALLOCATE: Inappropriate ioctl for device

```"

---

### Post by TheFu on 2021-03-06
I've never used MS-WSL with a GUI, since it is a text only solution to my knowledge.  You'll need to run an X/Server as a Windows program. The free ones are less than great, IME.

If you want a full Unix/Linux GUI on a system running MS-Windows, use a virtual machine like virtualbox and install a normal Linux distro.  Gnome is fairly bloated, so it will likely have bad performance compared to almost any other DE in that situation.  Be certain to provide the maximum allowed GPU-RAM. The default amount is fine for a Linux server, but not for any desktop.  You can change between different DEs in linux, since the GUI is just another program. The only trick is to avoid conflicting user settings. For that, when you are trying lots of different GUIs, create a new userid for each DE you want to try out. That will prevent settings for each userid running a different DE/GUI from writing to the same files.  KDE won't conflict with Gnome, but most of the other GUIs are Gnome-based.

LXDE was replaced a few yrs ago by LXQt. They changed from GTK to Qt for the libraries used.  Qt is what KDE uses.  GTK is what Gnome, Mate, Cinnamon, and most others.  Of course, you don't need a DE at all. Those are 100% optional.  DEs run on top of a Window Manager (WM). Running with just a WM is much lighter, but takes a little more skill than someone completely new would have.

BTW, when following a guide, maybe follow it exactly, get that working, then try doing something different.

One last thing.  By running an X/Server, you can run X/Clients on other Unix systems. Normally, we do that only on the same LAN, but that isn't actually a hard limitation. It is possible to run X/Client applications over the internet to be displayed on your local X/Server. Depending on the bandwidth between the systems, it could be an ok experience.

---

### Post by javierdl on 2021-03-06
TheFu thank you so much for sharing your insight about MS-WSL. It will help me to lower my expectations of it, keeping me from a disappointment. So I will try to get it working mostly out of curiosity. As opposed to expecting to replace my dual-boot Linux.

> [COLOR=#000000]BTW, when following a guide, maybe follow it exactly, get that working, then try doing something different.[/COLOR]

I'll try that then.
I already installed Gnome. How do I uninstall it?

---

### Post by javierdl on 2021-03-06
Will this do?

sudo apt-get remove ubuntu-gnome-desktop
sudo apt-get remove gnome-shell

... I think it did.

---

### Post by javierdl on 2021-03-06
LOL, it worked with LXDE!
I cannot say it's a pretty distro, but it works!

---

### Post by javierdl on 2021-03-06
I don't think I have access to the internet though :(

Also, I cannot run Software. It says: 
"*Sorry, something went wrong: Failed to connect to system D-Bus: Could not connect: No such file or directory*"

Advanced Network Configuration in menu://applications/Preferences won't run.

This is what I got when running "ifconfig" to check the network connectivity:

[COLOR=green]lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 1500
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0xfe<compat,link,site,host>
        loop  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wifi0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.38  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::7d47:8a6d:593f:fc28  prefixlen 64  scopeid 0xfd<compat,link,site,host>
        ether 94:e7:0b:51:8a:d8  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/COLOR]

I haven't touched the Firewall, maybe that's the problem. I just don't know exactly which apps to let through nor how exactly.

---

### Post by javierdl on 2021-03-07
This is the summary of the steps I followed before:


[LIST]
[*]
[LIST=1]
[*]Start by clicking      Start and entering "turn windows". The **Turn      Windows Features on or off** item should be displayed. Then scroll down to Windows      Subsystem for Linux.
[/LIST]
 [IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZ0AAAFtCAIAAABTLyDsAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAD7PSURBVHhe7Z0PcBzVnedbGCzzz/YWf IAsbGRjBFDlgOvb5GDE4fFIDl3salDpLhs5ON2Jahs8CxX3l1vmeU4XOvsqiolebMLUq5Yi9rjgpzC2rtYwjZgKOJJ4gUugJiAJWwDhhibP5ZNIDJ/dL/fe6//v 7pnhlJPT3fj6fG3e 9fv m zu/3 vpn2rGx8cNAABIEaeo/wEAIC1A1wAAaQO6BgBIG9A1AEDagK4BANJG4fuhe/a8obYCWLp0rtoCAIAEEKZrf/3X//Kd73zthRdGDh9 XyX5WLRo7rx5cx566Km//dtvqyQAAJhSwnTtlVcOPfHES2onmA8/PPnNb169aNFFah8AAKaUsPU1kqq33nrvj/ 46cILzw96Ue5ZZ02HqAFQWdSEogpNCtTcc889p3YcUGLRPSl83 BP7m97 NVu52vlrEbr9flbd6tybgbba9oH1bbYW9o1onZU3kjXUmdiGO7DywBVaFPeqgGoFMhX06KyJ4tnn332mqVf8Ugb7VIiZan9mATqGl3w99xzz2mnDV/20Rc9r41P/ZV8qaI6mla19fSbwjayb8jI9W1X8kF7jQ31Rt3aPeN71tbJtMmnsXNYfYqRO1F2eQUAGFdfffXP9/zMKW1S1CiRsmRKXMLstXvvvfeTT qvuOryP1x29cpvfOO6665bcsWiP//W5/KlCgVR39A4tE KwMj2vkxnp5EfNveMlpVTpmcAgKThlLbSRY0o4IcuaTzz7Bkz51 4sOGyhmXLltVlrtr7kkuSTrnwPrXloW5liyFNNBayhpULM8p G87nMgu5Dsv8ERtdyjW0LSJ2VGXKPpVCmImE9HPpYNPhddhTVIxT7dIOpzgAX1mqTsEJtNfcY Sy9dau1VNrmzfa26kaUYO3wjidAaDKsKStdFEjwnTtyZ9uC3r3984uN3Dh9 /7333nnnnd 885vDY6f0P3X B7X/jQocmvfO8eOyrJ 6hZmcMNGG82yfkWMq7LfB/p62VU2yiE0um1/FPuFAWy7bIa76wfb6bGaA03qNvh5RyJk4Ptw51MxqYju8g/1DjU4prTcGO8zS493eJoVC2SpDNfe1SM90wNgoVKqpW xSn3oogfYG2qT36qvLQW6ooVeU8FUY1hlQRajTLgBVCJRGmK4dO PA8cwvf/W73xz/6OTL fwrr x77ZWRk8c/HquplQVOm372Z5/JTQ1KcUjIhH1W38CioxbXvDR2rhPXOh1jCPnjciqtbu2GNv5fJBqmKHKq0E3T4SVZa9kgbUTT1aWsHiF Guz1NVYZsQKolK65R oxm19yXxwQjUblYvsrDOsMqCLUaReAKlR9WO6n5ZCqjKII07XP3ps7Wm806bPTb2u3/8h81kr82YPuODj058 PFv//dzvVTgrv91x 9 d1IW1iAUZ3DfkJQidkzz28u/uKYcXpa1lU3cxrC1gse3JsjcayVtieD6tSlriiCpI6 x2RApw52NqkRM3BXG6wwAVYRzTc1ySEuRtjBd /TkJzM qv3i2LQza2e03vZf535pbv0Xv/T1Ky/5vXPOlAXGjfHjwY6oUJxsc5Y9QrG7MNOTzarFtUKwF6s80pGujcpiokTDvMvKqbZg9rVuJFmr4 2h/g7h IpSBOkJKZN5DyMAUbN0PxXD Zw0LEklczLJCWm2surYIBX/u/BXKIjUGQCqCf NgtKlLUzXxj75dMbM2iMfHRsd/WDevHnzF8ybe Wi2RdeNF5zuioxbvz9k vVtgZSmUbLM5NOpuVHFqKpe6Ctp5nduFajRfmhlMjLapxYw6tXap2KhS2npIyFrUdIHKEcyZr6bGZDgR9zcM2Gc8mtaZ3ab81nlL1G/bfuG7AbLLtX02 Y3XPiqzBGZwCYDOQJ6UdlTxaLFy92ippEShtlqf2YBD5HRcM7efLkQw/9eMYM4/zzv/CFL8xZsGD qadO/ e //P tDdrpk8bG3o/f/rbRo3xtbNu u53o4kVAABMPGH22mmnnXbLLatPfHTy/fc/PHLk6J7/98xP/rX3g9PeIlFTJYjqXegEACSUMHvtb/7mb9ROAK 99hq9X3PNf4a9BgBIDoXjrwEAQGUR5ocCAEAlAl0DAKQN6BoAIG1A1wAAaQO6BgBIG9A1AEDagK4BANJGzbFjx9QmAACkAthrAIC0AV0DAKQN6BoAIG1A1wAAaQO6BgBIG9A1AEDagK4BANIGdA0AkDagawCAtAFdAwCkDegaACBt4PlQAEBSyL18sG/3C7mXXz90dJR2LzpvVuPl81qW/37j5RfLAhGBrgEApp7R3/4u 8N/fez5g5 es/CzmRd9XjvbMMZP fjYtBOHTn1/341Xze/8s2/OOnOGKl0I6BoAYIohUftP9zz04vunnbzw349PO038VeJxfhcbNZ99Mv3tvV8 99Of3PudiNJW8etru/7ukdnt f1qLyr7f/xYEUcVz6H8iusemX3dI9mcSgBF4plJc1fsgEqFLDUStbG510pR83XrD7zxbt/t6ibX9SN/v0aeOnnDp2YeOL755KxdQBhYika6wd4uxxv36 S WXE41OiXPXrQij97c/MvvvDqm9pHMo2/pSw323HHvils5GlQSKwjOT9q7MBpVI7uWD5H6SpaZsNGP8nhsvoP9I0VZ9 fe2/Um9SDROzln82HMHqDDvFCKSrl3/l3zq0GvrCsNYsVRuH3vimutVfjm5/tq5xsgo/x15k/0/e2OvYWx5xqliJ14dMdZcexFtcd 6GxbI5GRy6HjemHXpXLUXl8k2LZOMZyZLm1iQEPp2v/DpOQud7ufq/zm8fPOv/933h3516KOv1c/kQuPj4zWnffp79VSYdwuRPD 08UtrjDe2O6yz114fXVI3y9j5pm0e5t7cYsxdCdsHgMon9/Lrn828yBI1evW/ AG9k7128Tm1JG0kajL3szO/SIXFQQUoUdfYH3R6iGxcmO6hMjRyP7ecVvIxV/x4lNOlJ6s3Q86 tM5pnR3avnPW6rsza4zRETNt/xujRt2sS8Q2 61mi H12950e95pDxL2IfRy1OZ0dXnXUaGday7xyJo9I KaW1/aa4yub6UCynN3NPfY/VYLznpUSZ7eq340aoy8dBUlcuXxJlwlqjoD2vL1WeI40DsPET5EJqgGbT daA/kRMdM3u/elWVAJXLo6Ki8 ylFTW6QqO2 8zJ6//OfHLQSP58 W/7 oyATbK/RBfnMl5xO694fPXa7cY1IWbqGch2nu8msG5bPMvYfV1cLmWZ1c2 4iMRudNvP5JBGd weXbL8Qq3vGVQ/XY0375y7VXrQdxsdJBYmlHXVj2aprCdu3LR/j7yW2CO2jUSSVxrOGztUfbwrHGF7iYdeW5fLXJsF37rxWO8VS4xZm3qpAE8CN7d77vOyuftmrW81Behno6u5jKhnxRs3cx9m3dF9y/N/Osuou4LLR3G33RMe0FaBPhNBcyKJ8CEWqMF/YlgEHeiZyTvcu/JYULG4RI3e//nbC8hYW96Zf2rfcTOR/pf/FWai/dC5W/ SV8FsVizd a1ZYuuiO mKtfTLwYKvzF1iKsiuZ94wFsxcIMRu7 63uPCht7aNzFr9FVmJD339QobuMy hixoeoCzJoXyHM4uk5O4rluwcYtPG6RGzvF6xaYWprbyyIxxh9xLP9d8qJD3c3KxNd5vFGhs21akmFnzrmjvMqXJLaiwcEx7UVsE h8yJpOCHWLAG/4khKXwgSBsXnTfrlI POUWN/pGl1v/C x5RO2VslAqLnQJMsK6Z3qLFknlnqy26kufO8twiUFx04WplnVlmkRQ7UfiN0b3GrDrdRUHo6w9Zj Pa3FkXzWwwRl99g7dWrlAeMXm ZCHece1cqa18K2PFl/jau6hh3QrhCgW7Yy64Oek6yddj60eMPLnVAtv/upubLwbnhAe1VbDPYXPCFP4QC9XgPzEUBQ8EqaPx8nnTTtBVZosaQZbaf3mITitb1Oht2m/fpsJivwDJu2/AmNaZZRYRfH6zucEWnNSUiYftJjZGyPM12EKcO0toKzvCUm25jLhZvHWBWALTeWQ THfYfAnb51D2OqfPWK6bfNq2iugzABNFy/LfP/X9fTWffeJUsfF//MPxf/pDp6jVfHby1NERKiySClAGXbPMDeK11 3tUpBWwA7LLGKk9fRzy4KLAemR47YDYfeTs1y3X11uGrmi5BHn3tpmzL2B2mRDkgqfeHXE /MCVoreCB6TvzmJsCi3mitofGMkmKgTHtSWSWCfw ckCkXXUHrToNJovPziG6 aP/3tvbaKyQ2JXFMbH59 9Lkbr54f8UHREnVNGFY/yquVoNzPb94pt0qG17ZGt 0edbo8YtXpjWJ 4SEc2/X3mW6Xs5/slBlb7rbuyo3ef99Le1dkzKUucb i9w1D3abg8eZ7h8StDJF/KJ/9saks7EMVwt/c34leOa/nQ/nbHbc13I5enAkPaqtgnwvMSQSKrqH0pkEF0vln3/zyuZ/WvpUjo0yI2njNHT nl2Wp1b7ziy f9zkVE8ULU6q9tuBb12yqe NmuYLzzJf45l15IOtsdK/n/gCLXfDSTBiz7ui cZMh3C5fP8lsef5PR9UQrnts2/Ibj9lL2kJHRoQTKljwFf7ZsPNubP5H1qLY6KbeGwtegdQc3 60mpsnqhK3MrbcLRLvMx5w qFivZ/Li WwWBOubytCn0PnJBJF11B606DimHXmjJ/c 53my86csX/gtPfzp4yJh9bFjYLT3v/1jDd2NDecHf3hUALPvQMAkgLiFAEAgJ5k3g8FAIDiga4BANIGdA0AkDagawCAtAFdAwCkDegaACBtQNcAAGkDugYASBvQNQBA2oCuAQDSBnQNAJA2oGsAgLQBXQMApA3oGgAgbUDXAABpI5Ku7crO9rDifv1fMppsZM S0puyQEMqbTz7719RUg1Fd8B/YMljMZGfs5Py1Fs6smcJ6Y2zM/E6VvInVepZV2Yi6dr1nccEW9cYSzY9z1s777DiYGspeZoisSt785Y1Wwv3xmRyejWZ6Ea04I6dakbSM16cgRFwdiZux0omYWddpfuhSy6N/8cOACgfiToDnZ2p6kujBF1jy1ORNf98kIAEYtxt71V8kMp35b27yRzVIFVEIk3q88Db/UU7bC1Qwlq1bUIXZ/VDn3gXb5aL3SVGijGbuoJHgUJr5KI7ViZTmTPCOykMPx5MZrxnhNpdkDKdAZlSSgph1JYVXJUryvcmXfeSsC3nosPGN3Vmpt80aKzkC7cjESd8c0BFddYBQywdFJhRyC3Q2RGTKAiaVoXduVvWp9Axm6xPOb8jc7J5CcBtNf6Az5 8V785c YJbYu/7VlVzV1jV712/2zIDtg2zp0LYizF/qz7bVwkM5ttWQ5dwHxu2VpkKToLGHjUKxa7N5pOxFeCueLDpLrCQ6PHxE7lxvuxaeOmXi3vUdBs2CYyAFOyOOYyj9ZoOaUklmVc9vMtbfLsbnnz3yYbY2cEPkPRlbo/t0OAMJNXZnZ 5wd8xP0GdHFByFLOacOifuMQaedRNOsbq2fyRvrFkp 7rgjnVr9r5q/oXLyCxZfYM16Us23Snqun7lGiM/4vwECfV9Qd8DwXB/xLeEKKh6E VAL2avtBVKAsceOgrJJZcu2eK4BAu04s7av2Pb3jXrIl71HjztWujrXLLpAZFkDSRyZ7bdzpeF4yQ2q7ImSj9713duNW6eTaoW fwP/BSik74zMBohJ1LUUTinLpigs27iSfz6mvn1z19MS1RaALxOqqCrI8aBQbgrLAu8vHrsAeN2Ok1MyzyklfJ1QNNuXKJ0Zi d8QEXGV8xFUnKzsDClG8UZTjriqRYXVtQ12Bs2S77uv/ ji3mt4cGEm3zVN 1Pc4Xl C1V/fKBVD kpFJOkR/XLZ6gQML9cpfoUWMseuhj5vOEbYKCrXiylpww olAYWjYbdrEbHOqJ1ZsvqBnWR4Ob6i927bIbaFjcATpZ894YGS53OzPP/JQij0NR/jU8AZ6CbkQ489isJozrqJp2h77fpOduzZPJ3t8TwYsuaFNctnKRvKW2TJ7Qb/wfZYXH/nJkPYxbe/2hD2dcH9kQUZaldzYKxe Sq0CR 7A//lqUz62VetbxCOQIFW3Fl0hmxtMFNEWeeI/Dhyve1a OvUEqUzCiq6epu1ZL2k4VX uuaGlY/pnz02CfLsB9Jn5l4oC8NfjxOcgSaa74iQDz3KKMKJctZNOPi7yBMIfazbV06iAwGAj o8CRO/vlbBkHcR20UFoKxU6UkIew0AkDZgrwEA0gZ0DQCQNqBrAIC0UbSuae4eR8N/YNFVBUI1em5f23CeeAhw//3mU4lWByL2xF8s4oGJZXL6n4BZoi7IT1/te4jfwwIVTgz2qTtVJOCjDCWN9trzvya9bktT88dMRvWWBFVqlOijg1k3k2RVNnpPKYOKGw6oTBNY NRN5ic1eaRQ1/bv2GasvvPO1Yb6pbsX etpUJ2U/dPH6ZREousa274S28NLYjQbIWs3LFhwg1/Y6LCbHfFbQr/T/L02U1bcPyITvJQ0BLG/S5WnwtahutpUl gYhZ3gj7fjO4yhkmoq7FRf/9316w6ReIdJaHsi4dJ2BaJg0DwE9EQmyFA5RMRe0SHOT19iJ9qHRzqrCV FvmLubnvaol3n OQ2b0SIU2SV15aI25BI9H9Y/rrNFP0lYJe3DgioeeKJqGvUZX5eg59 tZ/ATWQ0GyVrZKv7hc0ZyyXcb/APxO7PA8Y23TOGpQ/Bns8tN8XWyGzi2PR 47A8h44 3oY8W448kw/k/TU7//EIl/mDI9KPKPeH5IPdwofjbqfcTGP5P6kYpQOSIxUq/s/jsmPso8aGZe4Kmw4Afkb0tLlDhFJlE/XC3hYZr8rdtTqrsE7Nxop8HEEk3X JHXyohmY8maFLYiZ1IzkJG8GcmGuyNKuSl9CM75NOPAhMwtQV Hcp93JL54O1Fjxfg TUJTvw/9MIngyD UooRt13bxXKgb30wSupGGhcoJ7FVBfPOgnXk/UT ggkSIU2QR9cPV4pxA34flb51SQi4BLh/zNJhIyr6 FiWyyl4abcD5wdNTAvT9tdf8NGZftX6vFfUgPlEGoqXEIYTg7pJp8vL3Y8gDybzGXFSsmIj1FwM/304mAN/gKSRO4v J60lEIp4MRX1AYRRqt gPNxJFXwJTTzRdCwls4sQf5ER/4IRFsyGvRljfJnQ FSVsmoHUNZhmNHdHpLkpbgiR8XcpTgAZOv9pLuJ9XcaJz MbZgHEIsHmzZZt7cI3k0WEyimqV3r8M68l9gdUQpwiN4U 3KLCNPlbp5SQS0CUjzbhvst2Aohor8mFIWUHBV R/sgqgQdS0bJHs2FZc10oQlaLETb/QMh/XCOjytxurNb6oRMWkEfi61LEADLKFfLHiiHHQJi2QR npn7tIf5hRoBclYYtW/TRa3wzWWCkJfaq0Dz4Z15PlA/I2RZ7a8XGKTKJ9OEWbEiLv/XwSyD6hE8GeO4dTA10Seri51Byx6XPF7qvA0AoZV9fAyAC5Kpo7hgAUB6ga2CSIWdcuCrytiMAEwD8UABA2oC9BgBIG9A1AEDagK4BANIGdA0AkDagawCAtAFdAwCkDegaACBtQNcAAGkDugYASBsFnjfo7 9XWwAAkBhWrVqltnQU1rXW1la1AwAAE8Do6KjaigbpUoXp2okX/ P4 LjB/wx p23HBr2dMuPi2Vf8IycCAFJBRera4sWL1VYozz77LL0ff E/zLzwFlYy43OWMXpnVbPf33v9/56zZEAeAgBIAWXXtUm6b0CaFY4qR0g7LUDURLosBwAAehJ3P1SoVoiofR4ma4PtNYr2QWtfbjoY6VpaU7O0i/8Eon0A4Sso4CK6HPNQWZENpdvFRVMSVc7KdjVtZyo8LfoKc8XWELxd0OCtOdpRTuwWiyJwaACUn T9zoN0K1jUxG6AstGF12wMjAuGG/apq6excWij 2oc7Mjm1CbT2DksD kcavZcckKV o02tetksF21NZDJtjrqH naONS5rkluLq2pz28QlRO9xnbvBW02PT6 Z21dQP8t3IXr1u4R/0eiQM3RiNWih7J0IB7xhRukiCJ1bdfjT2zWQemqRLHQmR8masbnQbJmDOdzjQ31crtu7VqhLUQmY/Rtd5zgg/09bW0aqapbmDGG9rmuBL6Ux7t1bjxXskq00LSu01H/yPa zAZx8Y90tWYzA PdZjecXdIT0P8yMHE1R2TKOwAqkGw2q7biU6Su/Tr/8nd1ULoqURKBohZorBFNq9pyLttJ0rBuQybbYZoI0p4KkiopSYUZ2TdkX6cLM7n8sNxmWZNyR1s5pXxRCeh/ADp7RNiXGl8vqOZhVd6qyOcscivt7VSK9q0WxUaXKmp3wmxd5Ln7pumAs//umgc9vdImOgdrjZZLit4SzT1GLlsPr7dSkaJWtLSVwQ 9YsVfqK2yQMIVJmoh0tbUPT7c0kfnsv y7umXKSQ3RstKl3iJs58vBGPANq6KgzxcJWuMpXyBmE2rDgf1X Ip7Gewvb6vRfqqA4bb99bWnMtuNHq5MGmO0n0qJ49v67EqyA01UCnP1OSy VWyoHkstc72KdFr9PWIQg7Ch bE7NVwp2EroT/Rbk4sIFhyJ3tLDLRJz73UzxRMAU45K07aitc1cgjly7NdInRKhoja Oef0P ff3JClfYiPEc 0V3XD/mKcpGNhcdrk1nraw0bHdZAMQz2m0trAsuKC8ReMjOvPn3/Bf7CbsiGtLSvucfXuL/mxs5eMRUk 5YDThaPPF7sCRo93wOCRjVQ61i2YFVa3doNuhXJkKE5MXvFtViD8CXyYE1z2F1S11tQSVhC1tnZKTeKkLaS7LXVt/ EXgvm/4HcUKmlE2SpGeOjh1 YduqM0Vf hyqppW5tb2ejaaEJ6la2GH3bB 01fQ1UprGwFElcvqfySdnDtS8qrs3VhRj4 x VNrU2T2jFL7xme3V/uLNRpZWZGENj6fKhTQQpRIqaJW1xKV7XThwffejvr6fX/gP/JjcoReWVgLD59KJGKSd/98HsL171yfGXZGEXg12mtcWLW24vkL7TM9nmrNcHdeI/SIO5ElTfYF6dZAKKWnlpzWkKshXR47RNRrq6wi/nsP5HgO972N6ji4g1W6v7XEomRYaVXnmkJPBeP1TTAZpB86thsN9RPqduwnBBa4HSlygGq SR24u5lAmSjVPOipO24nXto48 li/PdqlIFdOJGueNj087tZbeVWEnTQvzagWKl168P0kgX7RRe1/A9N14cSry7xjIqRowmvkwsnD4KLriHEtrAl5TYrdL0WqsDL/2wvtfmKZuXn5SVbj98Gg1861dcXxrPhPbXmvqHmAd56ONFq8fqumA0n3G9Uuaxky 1Sxo2Zz RB6smlv 4PzWqbhVQY2GOr0ggfiFrAhpK/I5qs2bN990001qx8Gjjz565513qh2TxYsXu54o0GGVeW9v8zlz6SzViBq9v7P/qS8s Bq/X7tDHpgMBtuX7lsXX4rSCfmz/Ls9/TJgKGQOb2zwfrtoE0GqSMpzVJc1XE4S5ofSVQk3JFvhqHIEm2J6UaN3zlTviaKpG9edCf/uObYXDUA5SVw8j3d/2XzuvBVaUaOUw689M eSa/l9WaLsNcBGmvkcR5vz98hxgL1WpaQ/TtG7v2hS9hgvpqn/Wdl4i//VGDXGtDPmLN3GeQCAyif9ugYAqDYqNU4RAABMGomz1xAvF4BqoyL9UNftzmDk7zwQLxeAaqNS/VDSrHBUOULaaQGiJtJlOQAA0JO49TWhWiGiFhgvd9CKsWMS8BQ7FSzt XYbR6wcVaVZOeeUqxUAQDySd9 AdCtY1MSuXtnsGDtm6Isy/eQpQAdZuYLD4XL0iljtl1FtAah2kmevhYtaSLzcSSV OFwAwGSRzN95BIpakLEWhu0sep6BFiZScNxXUZ7K6CKvuqJNaHHYX94O NsNaAUAUBTJ9ENDRC2utIVEkSW0cV d5eu7gyKvRn0EUtsBT7vkQyO KwBlI5l aKCoFYqX64MDEYZEkdXFfQ0r7yBiDEp9hb52AQDlI5F aJClFjFerpdCUWS9RCgfLxxu3A4AAEoigfYav2lFjVLC4uVqCYkiqyVq cjhcON2AABQMglcXwsUNc4LiZerJziKrB5/ YDIq1HD4UbsAOK7AlA2Juk5KtcTBTqsMpUZLxcAUDyV hwVh8QNRZUj2BTTixq9c6Z6BwAAPcmLK4l4uQBUGVUQf218/OiBHUcP7jx6YNeR/Y8fOfDkO/vp9dTh/U TnJHC0bsx7QxVGAAAfCBeLgBgikG8XAAAKADi5QIAphjEy0W8XADSBuLlUrosBwAAehK3viZUK0TU4sbLdSVTSoRiZnwhL3a8IbMIHSW2OCfoKADAZJPA33nQK1DUxK5e2YLj5apdmVKwGD/11OrTKFYuRMcFoDJInr0WLmoTHy Xn2jP9W13iQ6i4wJQSSTzdx6BohZkrE0siI4LQEWRTD80RNSKkDYzrGM0GRnp2tjT2LLS41QiOi4AlUMy/dBAUYsdL5ex19dCZUTJXz15nP61MkTHBaBySKQfGmSpFRkvNyKW/PnUD9FxAagoEmiv8ZtW1CjlZNx4ueUB0XEBqCQSuL4WKGqcFztebplAdFwAKgfEywUATDGIl8u54h0AAPQgXi4AYIpBvFzEywUAFADxcgEAUwzi5QIAQAEQLxcAMMUgXi7i5QKQNhAvl9JlOQAA0JO49TWhWiGiFhYv1/HrfXfgRpkXI6qt /Ay4K w7E24KUMIX qhhVVV5G7LoydyiAAEkcDfedArUNTErl7Zmla12c mi7gaVnBI2uM4Q7Gj2lYy5RlsaAxhL07JG2xv7uEAAFUz3yBRJM9eCxe1kHi59Q2NZhCgke19mc5OQ4UJoj3DF1ANxEAXQ7ggUUPWAVB2kvk7j0BRCzLWmLqVLYa89ljIGlYuzCj7bTifyyxkWbMMCrHhimErMEPdLu3ap1IIO/6t8nPpYNPhdVgoVIxT7dIOpzgELm XVPWJ/watzni75 jI0vZ2Slu6NKgSMRveLtkJ1lFWVXY1BaFjFHwQ7VlBgNutbdX5Ai2KrprjpX2ruD12AOKQTD80RNRCpK1uYUZGchzOs31Gjqmw3wb7ezRBvD0xbInBdg4pyWm9Rl PKORMFPE8 EKzHd7B/qFGp5TWG4MdZml/7DUz3qSCrnxCREAy3Wfu6QbpuOWyG41e0ajpAeoj8Q41UKk9e/SVCLxd0oxIIKvSR4zTxhC2/wIOR2ZyBgHutraFGxqlRXO8VFlzTavYdHw0AMQjmX5ooKiFx8tVikNXtrDP6htYdNTimhdfDFsup9JYbPh/kWiYoiicMdZN0 ElWWvZIG1E09WlrB77wnVjxa2U0JUvcMmk6gAX7hXaZDUqVgyVMjoi8Sqx0Vci8HRJOyLGH/ucUC3qYwgrg00KdDCRWjTHyx HY1AILwyKIpF aJClVjBerlCcwX1D8jJixzS/vfyLa8rhZVlb2cRtDFsreLxaT ZeK13ukT26pnWdQ2TwkE1E9fk6yqpgEhKJN7iSYrpkYWmxz44jX7HZEP0Z7mxUaQAkhATaa/ymFTVKORkeL5cVJ9ucZY9Q7C7M9GSzanGtEOzFKreH3S6RJuPfKg PU23B7GuVCkLbQ/0dwvEVpQhSErrWo1saorqODpf mqv0pJjyT2EVisRrVpJx qAWdpf0I4rPcD4nzWDuoUwKoFwtAhCZBK6vBYoa5xWIl0tXd6PDv2FPxvKBCtHULRZ3iFajRTmJIv6tCpPLy1vKbGERySkZYmHrMY0kcy2dHDetvugh7yzT0 M6ojGTZwtLeICy0UKReLlPVIlvsN4u6UcUGzIQZW9a8xllr9Fsy/sGnr6VqUUAIoN4uYmAxKd/leXs0d7GhmH89AtUC4iXy7niPUXwqph7sR8AUAKToWtkiEVBFhaapRc1kS5zuVAqED/VIu9M3g0EAJSD5MUB/0WTssd4MU39z8rGW/yvxqgxpp0xZ k2zgMAVD4VGacIAABCQLxcAAAoAOLlAgCmGMTLRbxcANIG4uWm6WYoAGBCSNz6mlCtEFGr3Hi5/kcESmglxlgk1JZNeccWdSCxxE/CBG4J9HO0 TCaqR5N03IN0KFjWxq1e2pvTHy3XIhz2W6OJoBxSZxFnQ9rkIhhduEF3nR7K84jWcz5khAfCQFmCSZ6 Fixri5VYpTU1Ssfgpej IzQtcJPN3HoGiFmSsMSKiRQXEyy3QitWIp4eUYgWkpSKyaWdiF1VhN roWiC obkPs7bFRrTpoqIK1Ul/n0W5oKb9rXjQRAklc1zFiQs8ClQZyfRDQ0QtRNroq1zGLExmvFxJUCuaWLjuHjoD0lpVOxPXrg2Jmsuoi58QUhIUxlZLxOniDgn8QXSd0xHUtL8VG6WEjvAAJuzfCgYyEf66DKgGkumHBopaJcfLFQS2YoqOIxaut4cFcSmu/0F6e32NlUE7tECiTRehDLbQILqBTYcNWanXqv5gs4wOi/3XZUAqSaQfGmSppTNeriQkFm50wkPvTjxkU010EF2OkhcmwdGCiIKUk0B7jd 0okYpJys9Xm5wKyGxcKMjeuYJvRuAfmj0zWCqBpm94n892oFEDKKrbzqUwUFZXHRLtuFYrZNwVbiBAJgErq8FihrnVXy83MBWwmLhKtjPMtfgLdyJ5NZ5Q 8GoR0au4WyezX9hu1datANJGoQ3fgRdOv3bRTFycM1vH9CxjHpmr8uA6oRxMtNG3SVa9bWAUgwiJfLueId6CBfDKF3QdUzGbpGhlgUZGGhWXpRE kylwsBN KHEAi9CwDi5QIAphzEywUApA3EywUAgAIgXi4AYIpBvFzEywUgbSBeLm6GAgAKkLj1NaFaIaJWufFyLcpbswO7ETkTEUdhFdOUt6rUVGTmTdh4ACiSKda1N998s6mpaccOx8MDpFvBoiZ29crWlPR4uSqcBj8xNRHRdOxnzqmNhn3Ox5aKZqRrn4gbpAsBNNiumkN0IJA4itS1XY8/sVkHpasSESBRa2tru SSS5YtW6aSWNNCRa3y4 WKwDwTEE3HeuacqFu7tiyPHNj10OTKDRM7qh0/FIroQCBRFKlrv86//F0dlK5KFMIStY6OjtNPP12lKgJFLchYY0QsC3F9sZAlN16uk3iV 6vnMu3tlNY KB4w1xhOw9agvMOM2EeBNYcKZQILOLRHaPA2ACaZMvihV6z4C7UVDHma5G SlsndMFEj4QoTtRBps66vJMfLJVXZ2KMijsSsnMtrwuoONfSK1pq6x4db jiahkOuctmNBmW7h mvpADkc KpU1BBFK9r5BDKl2dbC3mapGKkZaRoYaJGAsaVBIpaJcfLVRFx7Wg6cSvn8pqwug4XW4S1FCGATGlr7JSPizqHqakkBLbuNjYMIwAQqCBKstdW3/4Tei2Y/wdyQ6XqIP0iFZPSFiJqiiBLrbLj5VphuENjCIVUzkQIq1u3trez0b6FoiF6bF4StVay9/yi5vQ9 RtB880BwJRRvK6dOD760N9fT6/9B/5NblCKytNhSVu4qAmbTy9qlFLx8XKdxK1clA/0HAe7zBwSQvsWgpfwSjywW 0JUWmu rFlqhzmjmy5vzkAKI3ide2jjz6WL892CKRlPxQEWmqEVDGdqHFexcfLdRKzclE MKxu08K8yrE9XR2hlbhhn1UFz2Vc/jWJ94Ah8vwBbAGYYop8jmrz5s033XST2nHw6KOP3nnnnWrHZDHi5QIAgknK86G7Hn9C 5OOyxouv/6PrlM7JrGeD33vl83nzLtRK2r0fnj/03MWfJXfoWsApIX0x19795fN585boRU1Sjn82jNzLrmW35dB1wBICVUQf218/OiBHUcP7jx6YNeR/Y8fOfDkO/vp9RTZaCRnpHD0bkw7QxUGAAAfibPXAADVRhXYawAAUBqJs9cQLxeAaqMi7xsgXi4AIIRK9UNJs8JR5QhppwWImkiX5QAAQE/i1teEaoWIGuLllgT3I/QZAxcxZsxN0QdK7NmK3lcHJbYOKp8E/s6DXoGiJnb1yqaCeUhE1AqOhWHu8fOS6Y6XG4WRro1DbW1D4Y HOjQ93owVfaAbUqUSA/9O8QcNpp4ida0s8XK10MkcJmqIl1sCYiLWrZPRjxLLRAT BVVGkbpWerzcUAJFLchYY/h5cXnB8vVbCfFy XAV7Zb2fA0JfBV6Ezz7IR1Q m7Pk8J5CHWpuUcGaOPj5QC5gF2bOWj6X6FK g8U5e3qrUpErn/ JWR4 wP/eofFNYipW7pU0zdH6/4J8SWA9FEGPzRKvNwYkHCFiVqItHGkIWGiVUq8XMKKdqtpSFyCVnBbWaEv2q2nxZAOWGarS9g8TTR104xIl9k nk1My8fn6RSxSqioYKCN4x5pDyS04yL882/hD/zrGzUjp27PHl3fTCJMIEgjxeuaM0auc7tE6HwLEbVUxctlTIXTNkS15jzXqS/arafF4A5YsiaFzQw152tCi0vLzYjgZBXJfog9PdpxMb75d8ErZHbgX/ oGXPqtH2TRJlAkEZKstdkmNwo8XLjEWSpVUO83MK4o916WgzsABlyOfOCJm3NWREto9G0rpNvN/CNBzmbZAmp1f3hTs fqioXrsC/ITF fX0rQPRwwaBSKV7X4sbLjYiw fSiRimpipfrRNsQ1d3ojm0rivm9J0 Lmg6QDWvpKkP5ojl/EwGIMXd09JnxMq3VfbaJOEGPfgJD8Qf DRi1hbdvFpEnEEwtr8VBHRNK8brmjJHr3C4VqWI6UeO8VMXLdaJtiARqIGMaWcL 8kW79bQY0AGWNYfyyomSwuZvgtftKcFt74kx9/RkzMnkvxoqDmvNZ5S9pj1QP4FhaAL/Forx6 mbTYQJBGmkyOeoNiNeLgCgTDz//PNqKwKXXHLJRD0fini5AIBykRRdmzgQLxeAaqPsulaG36 VGcTLBQCURuLsNQBAtVEF9hoAAJRG4uw1xMsFoNqoyPsGiJcLAAihUv1Q0qxwVDlC2mkBoibSZTkAANCTuPU1oVoholZN8XJjdDgW/tE5uyfy7KajTYVdwRT8hJ87y826RlFcP6KNFiSdBP7Og16BoiZ29cpmh3UgRNgGOxZPhcbLjdfhEi9J /FRbjJW0/Yz8DS8iBFuyycgI12t9gNa5ij44a0gZQtruql7uKVvqsIZg7KRPHstXNQQLzeBTGmEW/2ny8 3x4s8YEKfT8YbEQ5UGsn8nUegqAUZaww//Cz1gk/1VMTLddfvyXQlUUlnuFpdeTPFNbpAHE1baPogEA 8O4wcLmeXUDXF6q04ZlAlUpKV7T/kvLGWHSVbm3adpXyJYJxxckqFCS6YeGiFqItNF3tAwUmJp4uRb KK90sVpJdLwnXK2/vHZ0TsSl7r7A3fjrtPBEuGWT1FoTUArjmpmCvSVy2Y0GTQ0V7GmuaRWbuuC61peWxBwF cXqA/BUXu J60tdkXki6q84wjqPQMWSTD80UNSqK16uBedaV6yI8koNhsS51ZTXjc6Fvb6mBMGDv04XvCAnFFlIm0v7RbshM6OvubGzVwyPPyBHaNwC3qW1vtawUdp2BbrNuqfy1D4Bg63iSaQfGmSpVXW83LhRXiciKmyhOu0It74YtmEzQ5S7t/QZNVoiFlw5Wb2aqL8eGxBUHgm01/hNK2qUcrKq4uVaiFyX68fXbXDcV0153ehi4a/Twh/hVnRQxLB1fanoZyak5sIE2FZWR8Ir10b9ZdtWY GDCiKB62uBosZ51RUv18If5ZUkIiTOrb 8dnSx8Ndpoolwyx3ckOnpsabBOzPhvY2O0E/77rLpcvIcyo5opsJuWhP1F ZaGpik56hcTxToQLxcHSQG/avK50ZOMpPUe/IlW43eyD 2K0SZqwNRqNTnqEi2wlHlCDbF9KJG75yp3qsA/qsEFesQ8dKa 6/eTRB1a3tb urjWXmBiNvGMU1tkDwQLzeR8K84sjm 1VCJhoPsfYV2HkwBFRnPIxbv/qJJ2WO8mKb Z2XjLf5XY9QY086Ys3Qb5wEAKp/06xoAoNqo1PW1ieX7l9XU1OA95e8ARCZx9loR8XL5pP rX6sdkEbGZ63GR5xiKtIPdd3uDEb zqOYeLn0fT6K5bZU8/3L1DccSCOV6oeSZoWjyhHCLAsSNZEuy9nUrH9FbYGUMr5pkdoCIALJe46K30JETRMvV570bd9eNHClTCBmDmya3zlH7RhXXjj 7ZnGnPOGnYlhuA8vC9SHTYvE68Lgn/tPQLulIPt813n2o5OF8Q0hxrQHgq8uEIsp1rU333yzqalpxw7Hj9FIt4JFTex6lU2e9D1DJ5oyM2WKMae23qhd eVaudd4/vSRI2PG4aP16w9kD8u0yYWu7VuM9vWvUFdruk422Po7EZRLHGcO3HL24COv1PzgqPXoZDGUY9phr4FYTKWukai1tbWRt7xs2TKVRGdwuKjp4uWqk/7wyZHza6Vl0fjls4Z3v2ecL3WttiVjbH9xTGxPEXOm1x09OSS3Dx/N/kpuJZ xfVPyNeAD9hqIxZTpmiVqHR0dp59 ukpVBIqa31gj1El/ Ph246wWtlNYyPa9ODZ8 dnC46tdeN7JPF fliEjNlYox3B4hTLrhMfkTiHMRHpJP9fh8DosIypGrq5R23mXq7DiVycGzzun11mty6pyW1jebjjr5G27ZvIT2Ul0FqCqLmgyateuXcSuN2H3X/q/oq0rVSJV1bhivjzWNWoupupR6b55kFUNfJsOD/GsCWt0YsM77Vautc3DUblqgLDXQDwmSdfI0yR/k7RM7oaJGglXmKhppM086cfyR2oX8hVSu9D4sO/w8f6XpzfQ7pVnN718wheZp3bt SfYK3zkRN3yc9UFv/acYXK71r/SapxlPtdoJ9Z0vVd/C1 BtsN75dn1Rw3p7ZKFaJCre W5a4 8zYXXv9LsMsqON68/sD3DCuLSOw21a79utIrmjOUX8AXvqnMs 6Ttbrdlzh588mjOVYAaenvQGOvqeqXmX46L/p 1nbYp9xFjnSmUqolHTjTdsqjXEMfa8yCx66nfSaauZh4EtfXc9FuRAx/5p93PWPYHbw9zLjnCRrvwgukQlQlABCZJ18jTJBUjLSNFCxM1EimWrUBR08bLtU56pTgkZEfG6GIYOsKioxbXvIx1PU6XvbCkDCF/c2rrj763UYhRbud76ilqXqc70S8V6vDRjpeFbpoOb1tm vYnPzQyM8liUq4uZV1 gdvwsaDLVYpCuLSNdT0s1rOczTnrpA4rO3TmqvNFh0MaFeuMbLuRiXTL2XXKMTeb4LGPKQ/dmgct2nlgzMOj4pt2PcebHzG6N11gPKIUE/YaiMUk6RrpF6mYlLYQUVMEWWoB8XLtk14oTtv50weH OLJvfihcf7M8i uKYeXZOXDvl/R9vTMnJkr2ULka76ezb0LAu2yw0dbd4/Z9zfCqG04X/zvrfP4xt3TyfJqXHFO/dBxqYChjZ5Q9yvoxRZcRQJ7DcRi8tbXLGkLFzXhZepFjVK08XLtk54V55zu5YZa7T48Nnz5OWvV4lohqPB552wQukCSofxQSjTOXiXFYs556y6XNstY35Cx8lYpK7Q9fdUfTTekxAhyOw8s3T1Wr4wjwZXnWY5bS6ZW2I9j 46aVg8ZmOJ/gXkbl7TyPNNEctfJep05d4NbrzWNEqL/pvtZAvp5KAvaeRAe6Pq3jVvUyh3sNRCLSb1vQFr2Q0GgpUZIFdOJGufp4uU6TnpSmTHjqDCdmOP9LxuGZnFNC/k vN5EtfUaH5rRvI43C8 REsd5oUq5Raws5ylZoe36y6criTF/pLZn ckOXpYy dXYQukMbpq/9sjbYsVKrJTJmjOGI3jY2PD5bHmN83qWaM5fJ3mCR8jXfk/9eMJbgEZt3Tfg/hvL1Z0BdSehGPTzEIDp XrvRWjxz0Nt510X1O9 t0dYpt3ivgHsNRCLSXqOyvVEgQ6rTBHxcqvw dC2by9aNeS5NZFm8HxouqnU56g4JG4oqhzBpphe1OidM9W7DX3Vq60qgTxBecegaoC9BmIxGbomHgAtjCwsNEsvaiJd5nIhi2o66cVP1cgTlDc0q4aqoCpZGKeLmI55F6EM8j1ZTdDzVI10LYsmULy0uyoVHI73O8p/hdfdggjTwXB6lLUqCCQBxwAMAUU5FxJWNRRLxcAEBFg3i5uni5AIBKBvFyvTdDAQDAw6Q bxAFoVohoqaJlysZbK9x/M1v2lvaNaJ2VN5I11JnYhjuw0uGqvMgare67Mo3s2zcXQk yh4gZbkPAqCaSJyusXwFi5rY1Stb06q2nn5T2Eb2DRm5vu3qyqa9xoZ6o27tnvGp QvkTd1802d8fKCN/4Q7b/n6odIdWf4UP 4ymgFC4EA1kjx7LVzUdPFyFfUNjUP75CU8sr0v09lp5IfNPaNl5VToGQBgKkievcYEilqQscbUrWwxpInGQtawcmFG2W/D VxmIcuaZbyIjS7lxtn2DPtxMmWfSiHMRMJy/0yH12ENUTFOtUubZSYTj3VGu809Ri5bb/bG2zsu395OaVPRWQAmjGT6oSGiFiJtdQszOWGiDefZPiPHVNhvg/09bascgYAkuWx FftvA225bIe6yOuzmQFO6zX6zHgVduL4cOdQM6uG7fAO9g81OqW03hjsMEuPd/uaDEWoj0NydCl wsuQ 2t6vtwbGktfi/RbB4yNSv9yQw29sTsLQLJJph8aKGraeLkWSnFIyIR9Vt/AoqMW17w0dq4T1zIdYwj543IqrW7tBhWimtfpTFHkVKGbpsNLstayQdqIpqtLWT1C/GJjr5SZGuNP8ROljIlYc1Q62NwjvwGoBnjoIH0k0g8NstQC4uXaCMUZ3DckpYgd0/z28i uKYeXZW1lE7cxbK3g8co9mXutAQbUlNOmjEkCJhpILwm01/hNK2qUclIXL9eGFSfbnGWPUOwuzPRks2pxrRDsxSqPdKRro/JDKdEw77Jyqi2Yfa0bSdbqeHuov0M4vqIUQeI23Gndw0gMYiym wlAmkng lqgqHGeLl6uA1KZRodrxU6m5UcWoql7oK2nmb20VqPF/FNJTd28rMaJNbw4pYwcFrackjIWth4hccSguhdRn81sCPxxxmRCM2DdN CxGBEW7QCodNIQLxcAUNEgXi7nincAANAzGbrGz39GQBYWmqUXNZEuc7kQAABoSeL62tEDO44e3Hn0wK4j x8/cuDJd/bT66nD 58 /NozpHD0bkw7QxUGAAAfiCsJAJhiKnV9DQAAJg3EywUATDGIl4t4uQCkDcTLxc1QAEABEre JlQrRNRKiJdbGPdRLswnCQTBT7ZrawipNjqOeEmqMrNazim9fgDSwxTr2ptvvtnU1LRjh PhAdKtYFETu3plU8E8JCJ2hYwgJPd0IT3iYgfPCA5gOzGwctXnN6jWx3uN7U6Vjh0HuCw6C0BymUpdI1Fra2sjb3nZsmUqiTUtVNSqMV7uSFcrR3WzA3DUrV0b7ZFXAKqTKdM1S9Q6OjpOP/10laoIFLUgY40RUTZC4 VKw0dhOqZsvPhixlJihCfDNbU5MHMDou/KI5yte/MUNJpc LP7DvtLV787MjCluIPoApA6JknXyNMkf5O0TO6GiRoJV5iohUhbwXi5muC3Ak/MWNKGZoOKeSOUeYLTBtUmCYq GxyxNiTWblQvWl /OzKwJ4guAClkknSNPE1SMdIyUrQwUSMBY9kKFLWS4uVqg98yrpixfa2OgEQu3MFpA2sTcKva6LvBEWtDYu266w4koH5vZGAA0s4k6RrpF6mYlLYQUVMEWWqTES83R0IQUUaKIjhibVCsXY4pZ98RKQQi4gIwietrlrSFi5rwMvWiRiklxcvVB7/10NjSu2fAiPA3CsJrY59YH303PGKtLtYuG3w9zQ6xG nq0spchPoBqAYm9b4BadkPBYGWGiFVTCdqnFdSvFx98Fs/VK6lr77QbyHCawuMvhsYsVbcqyA0sXabusUSnsznGlfqux4xIi5NC 4bgDSDeLkAgClmdHRUbUUjKc9RcUjcUFQ5gk0xvajRO2eqdwAA0JO4eB7v/rL53HkrtKJGKYdfe2bOJdfy zLYawCkhEq112KAeLkAgNJAvFwAwBRTBfYaAACUBnQNAJAgstms2jLxpxQEugYASBZOIStC1AjoGgAgcUg5K07UCOgaACBBdHZ2yg1L1KyU6EDXAADJwilkRYgaAV0DACQOKWfFiRoBXQMAJJGiRY2ArgEA0gZ0DQCQNqBrAIC0AV0DAKSNws 9qy0AAEgM4c 9F9A1AACoOOCHAgDSBnQNAJA2oGsAgLQBXQMApA3oGgAgbUDXAABpA7oGAEgb0DUAQNrA73JBypn9/d ordRx7KqLZ0PPHEE2ordVx33XVqKwDoGkg51axrixcvVjsp4tlnn4WugWpH6trrd5whd9PBvPs/onfoWhBYXwMApA3oGgAgbUDXAABpA7oGAEgb0DUAimX3 nkmNz14UCVyqrV38MGb5s1bv1vuVBSi5xLH2MqEc4omBOgaAEVB1 aaV 95 nXB09/46Vf9V ru9V/96Teefn3TcrVfKbCmfXX4e3Jor7/ A PJSlNm6BoARXDwwX94 NYtj952sdy9 LYf3GPc2 28/Ekc1hh2icrh4IN33XvpFocaX3zbbZWmzNA1AOJz8MmfPnfrCufVfvHXv3H1qwcsi 1JYapVnKVG IdmYrvdyrMW7uSDKtVhrto rCroS5hooGsAFMXV9fPVlsVzwwfUxr33Pnzr9yrPVFNohsYs3yT90i23PvwPpog9d /wCpn2nDJXScOE9y0Qwq7ccWaLYR05oUDXACgKS8RsLD24 p4t97y6ZmKXxicQzdAEymBb87DaJ66 p12YdstX3GoIc1WYey5JP3jgVZK/r6pDg ouL9A1AOLDXufDO13LaXQ9Xzrfupzn3/bolkvv/WoF3gr1D00i1wvZ6Hr6nqtVWmRuFQcKJsU3h64BUAQX3/a9Wx9eY8kWuVr3Gsp0MVm 6emKNNrk0BwrYQcffJC2Dww/J 1RVnCZoUPIosvZvHj pYY7ZeKBrgFQFMs3vb7FWCO8K/KvyJLx3/q8WBptFSdtNDSWZDW2eXcZXyfBXt5 jyG8ybuGLw2z19Sg5aFCHFng5aFW0kSDeB4g5SCeR8pAPA8AQDUCXQMApA3oGgAgbUDXAABpA/cNQMrB3zdIGfj7BgDg71GlEOgaAKDqwPoaACBtQNcAAGkDugYASBvQNQBA2oCuAQDSBnQNAJA2oGsAgLQBXQMApA3oGgAgXRjG/weaPYeWpS2fmQAAAABJRU5ErkJggg==[/IMG]
 [IMG]https://static1.makeuseofimages.com/wp-content/uploads/2019/03/muo-windows-bash-features.png?q=50&fit=crop&w=750&dpr=1.5[/IMG]
 
[LIST=1]
[*]Restart Windows.
[*]Open the Windows Store,      search for Linux, and install Ubuntu.
[*]Once complete, click [COLOR=#2F2F2F][FONT=Inter]**Launch**[/FONT][/COLOR] from within the Windows Store or open it from      the [COLOR=#2F2F2F][FONT=Inter]**Start**[/FONT][/COLOR] menu. 
            On the first run, you'll be prompted to input a username and      password to create a user account.
[*]Run these commands
            [FONT=courier new]sudo      apt update
            sudo apt upgrade[/FONT]
[*]While this upgrade is      running, head to Sourceforge to download and install the [VcXsrv Windows X Server      utility]("https://sourceforge.net/projects/vcxsrv/files/latest/download").
[*]Install the Linux desktop.      Many [**Linux      desktop environments**]("https://www.makeuseof.com/tag/best-linux-desktop-environments/") are available but to keep things simple we'll install      LXDE: 
            [FONT=courier new]sudo      apt install lxde[/FONT]
[*]Following installation of      LXDE, input these commands:
[/LIST]
 [FONT=courier new]export DISPLAY=:0
 export LIBGL_ALWAYS_INDIRECT=1[/FONT]
 
[LIST=1]
[*]Open the Xlaunch      tool, and choose One large window, and Display number: 0
[*]Click Next on the following      pages until the end.
[*]Start the LXDE desktop      environment
            [FONT=courier new]startlxde[/FONT]
[/LIST]
 [FONT=Calibri]
  
  **Steps to start Ubuntu / LXDE every time.**[/FONT]
 
[LIST=1]
[*]Open Ubuntu
[*]Enter these commands:
[FONT=courier new]export DISPLAY=:0
export LIBGL_ALWAYS_INDIRECT=1[/FONT]
[*]Open the Xlaunch      tool, and choose One large window, and Display number: 0 
            Click Next on the following pages until the end.
[*]Start the LXDE desktop      environment
[FONT=courier new]startlxde[/FONT]
[/LIST]
 
 [FONT=Calibri]Note that it is not possible to damage Windows 10 using the Linux environment. Any commands you input will damage only the Windows Subsystem for Linux and the chosen operating system. Windows 10 will remain safe and secure.[/FONT]
 
 [FONT=Calibri]**Sources**[/FONT]
 
[LIST=1]
[*][How to Get the Linux Bash Shell on Windows 10]("https://www.makeuseof.com/tag/linux-bash-shell-on-windows-10/")
[*][How to Run a Linux Desktop      Using the Windows Subsystem for Linux]("https://www.makeuseof.com/tag/linux-desktop-windows-subsystem/")
[*][5 Linux Distros You Can Install in Windows Subsystem for      Linux]("https://www.makeuseof.com/linux-distros-for-windows-subsystem-for-linux/")
[/LIST]
 
[/LIST]

---

