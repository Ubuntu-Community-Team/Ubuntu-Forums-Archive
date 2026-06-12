---
title: "wget does not work for addresses behind proxy"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by humble_coffee on 2010-04-14
Trying to download addresses that require proxy authorization fails for me. I get the following message:

```
failed: Connection timed out.
```

Also it seems to be trying to connect using port 80. Shouldn't it be using the port specified in the proxy setting?

I have the proxy configured correctly in the Gnome Network Proxy Preferences and everything else that needs proxy access works fine, with the exception of apt-get. It's error message is

```
407  Proxy Authentication Required
```

Anyone have any idea? Or should I file a bug.

---

### Post by humble_coffee on 2010-04-19
Someone over in this [bug]("https://bugs.launchpad.net/ubuntu/+source/wget/+bug/232469") found the problem. The environment variable no_proxy has a trailing comma which it should not. Once you remove that, wget downloads through the proxy started working.

Also, the reason why synaptic was not working is because it has it's own proxy setting (under preferences) that is not set from the gnome proxy settings. Everything else is playing nicely with the gnome proxy setting, so I had assumed such a core component like synaptic would. Presumably this needs to be set again for apt-get but I haven't looked into this.

---

