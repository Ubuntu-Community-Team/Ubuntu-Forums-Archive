---
title: "Uninstall from &quot;Add/remove&quot; in Jaunty"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aquascrotum on 2009-04-07
I upgraded to Jaunty last night and am going through removing default applications to go back to my preferred applications (ie Evolution, Totem etc).

However every single program I've uninstalled, when I;'ve gone to "Add/remove applications" I get a message saying "Cannot remove '*insert application here*' One or more applications depend on *insert application here*. To remove totem-gstreamer and the dependent applications, use the Synaptic package manager.

Using Synaptic is no big deal in itself but if every program I've tried to uninstall (8 at the last count in 2 hours of Jaunty ownership) is unable to be uninstalled from Add/Remove, whats the point of Add/Remove?? Or is this a problem with my install?

---

### Post by Stupendoussteve on 2009-04-07
> **aquascrotum said:**
> I upgraded to Jaunty last night and am going through removing default applications to go back to my preferred applications (ie Evolution, Totem etc).

However every single program I've uninstalled, when I;'ve gone to "Add/remove applications" I get a message saying "Cannot remove '*insert application here*' One or more applications depend on *insert application here*. To remove totem-gstreamer and the dependent applications, use the Synaptic package manager.

Using Synaptic is no big deal in itself but if every program I've tried to uninstall (8 at the last count in 2 hours of Jaunty ownership) is unable to be uninstalled from Add/Remove, whats the point of Add/Remove?? Or is this a problem with my install?

It's not a problem with your install, it is a problem due the simplicity of Add/Remove. Synaptic lets you remove it because it will also give you the option to remove applications that depend on it. Totem [depends on totem-gstreamer](http://packages.ubuntu.com/jaunty/totem).

For cleaning up the default applications I suggest Synaptic, then using Add/Remove your own applications. The dependencies for the default applications are a pretty complex.

---

