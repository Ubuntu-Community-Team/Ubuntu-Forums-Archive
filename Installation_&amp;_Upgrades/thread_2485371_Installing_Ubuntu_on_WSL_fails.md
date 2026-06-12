---
title: "Installing Ubuntu on WSL fails"
date: 2023-03-28
forum: Installation &amp; Upgrades
---

### Post by timboxy on 2023-03-28
Following the instructions at:-
[https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-11-with-gui-support#3-download-ubuntu](https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-11-with-gui-support#3-download-ubuntu)

and I get the following issue:-

```
C:\Users\Tim> wsl --install Ubuntu
Installing: Ubuntu
Ubuntu has been installed.
Launching Ubuntu...
Installing, this may take a few minutes...
WslRegisterDistribution failed with error: 0x80370114
Error: 0x80370114 The operation could not be started because a required feature is not installed.

Press any key to continue...
The installation process for distribution 'Ubuntu' failed with exit code: 1.
Error code: Wsl/InstallDistro/WSL_E_INSTALL_PROCESS_FAILED
```

Try to remove it in Powershell and I get :-

 ```
C:\Users\Tim> wsl --unregister Ubuntu
Unregistering.
There is no distribution with the supplied name.
Error code: Wsl/Service/WSL_E_DISTRO_NOT_FOUND
```

Remove Ubuntu using Settings->inst
alled apps and try a reinstall either via Powershell or Microsoft store
and I am back to the same issue.

Uninstalled Ubuntu from settings. Uninstalled WSL rebooted reinstalled- same result.

---

### Post by timboxy on 2023-03-28
Solved.
Despite installing WSL from the Windows store I discovered it was not enabled in "Windows Features" [Settings->Apps->Optional features->More Windows Features->Turn Windows features on and off"].
However enabling it here (and rebooting) did not solve the issue. I also had to enable "Virtual Machine Platform" (and reboot) in the same place.

---

### Post by ActionParsnip on 2023-03-28
[https://superuser.com/questions/1736443/wsl-2-installing-linux-failed-error-code-0x80370114](https://superuser.com/questions/1736443/wsl-2-installing-linux-failed-error-code-0x80370114)

---

