---
title: "Wine issues"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by ashenrose on 2006-10-21
I am unable to load any programs in Wine. I am getting the following error message:

wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found


I have uninstalled wine and re-installed it, I am running Dapper Drake. I tried to re-install the applications to the hidden .wine folder like it says in ubuntu help but it cannot write to the directory, even after chmod 777 'ing the Directory.

Any Ideas?

---

### Post by hellblade on 2006-10-22
Try to rename the .wine directory in your home to something else (eg. .wine.bak) and install your apps again. The wine configuration that most probably affect you are the ones in there and not the system-wide configuration.
If that works, you can remove your old and now renamed .wine dir.

---

### Post by ashenrose on 2006-10-22
Thank you.

I am still getting error messages and when I try to load a program (wine programdir/program.exe) I get the following error. 

err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
wine: Call from 0x7ee61430 to unimplemented function dbghelp.dll.EnumerateLoadedModules64, aborting
wine: Call from 0x7ee61430 to unimplemented function dbghelp.dll.EnumerateLoadedModules64, aborting

---

### Post by ashenrose on 2006-10-22
Can anyone help? I'm at a loss. I have tried all sorts of things.

---

### Post by hellblade on 2006-10-24
Please try installing the windows version of firefox with wine and see if it works. I think you are trying to run world of warcraft which doesn't run with the default wine distribution.
If that's true then try searching in google bacause I somewhere spotted a guide for that.

---

### Post by Aberrix on 2006-10-24
> **ashenrose said:**
> 
wine: could not load L"c:\\windows\\system32\\WoW.exe": Module not found


Are you sure that's the correct directory?

I know mine looks like ```
"C:\\Program Files\\CCP\\EVE\\eve.exe"
```

just for example (I don't play WoW). But to me it looks like your pointed torwards the system32 directory instead of the proper Program Files directory. I know my logical directory looks like ```
/home/aberrix/.wine/c_drive/Program Files/CCP/EVE/
```

also do a ```
sudo apt-get install wine
``` and that will make sure you've got the latest version of wine.

---

### Post by ashenrose on 2006-10-26
It automatically points to the system32 dir and I am unsure how to change this. 

I have the fully up to date version of Wine and I even double checked. I don't need any updates as far as apt is concerned.

---

### Post by ashenrose on 2006-10-28
Does anyone know how to change the directory that Wine automatically points to please?

---

### Post by VoodooDali on 2006-10-31
> **ashenrose said:**
> (...)
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.x is in your path.
wine: Call from 0x7ee61430 to unimplemented function dbghelp.dll.EnumerateLoadedModules64, aborting
wine: Call from 0x7ee61430 to unimplemented function dbghelp.dll.EnumerateLoadedModules64, aborting

This is happening to me also, trying to load a different program.

I can't find any specific references to this error in Wine's documentation, Bug Reports or FAQ's.  ](*,)

---

### Post by octoberdan on 2008-04-12
> **ashenrose said:**
> Does anyone know how to change the directory that Wine automatically points to please?
You don't need to do that. Just pass to the wine command the path of whatever executable you want to run. So, for example; wine"C:\Program Files\World of Warcraft\WoW.exe"

---

