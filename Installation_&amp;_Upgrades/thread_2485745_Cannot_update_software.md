---
title: "Cannot update software"
date: 2023-04-07
forum: Installation &amp; Upgrades
---

### Post by paintboxz on 2023-04-07
When trying to update software via this command:
sudo apt updateI get this error:

[B][COLOR=#ff0000]E: Malformed entry 1 in list file /etc/apt/sources.list.d/vscode.list (URI)
E: The list of sources could not be read.[/COLOR][/B]

It all started when I tried to install Microsoft Visual Studio.

Any Ideas as I am new to Linux

Many thanks for any help

---

### Post by ian-weisser on 2023-04-07
Start by reading line 1 of that file.

Does it match the format expected?  (It likely doesn't match. That's why it is a "malformed entry")

The most common cause of the problem is human error - whomever installed VS did not follow the instructions with enough attention to detail.

The way to fix it is to simply edit the file so it conforms to the expected format.

If you need more detailed help, we will need a link to the VS instructions that you followed, and we must see the contents of that file.

---

### Post by MAFoElffen on 2023-04-08
Currently, it should have two files with the following contents...

/etc/apt/sources.list.d/vs-code.list:
```

deb [arch=amd64] http://packages.microsoft.com/repos/vscode stable main

```

/etc/apt/sources.list.d/vscode.list:
```

deb [arch=amd64,arm64,armhf] http://packages.microsoft.com/repos/code stable main

```

---

