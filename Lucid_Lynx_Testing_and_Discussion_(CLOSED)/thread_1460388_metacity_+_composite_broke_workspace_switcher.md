---
title: "metacity + composite broke workspace_switcher"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by thil77 on 2010-04-22
under gnome, lucid, adding the 'workspace switcher' with composite ON.
I can't switch a task from one workspace to another (by drag and drop).

When composite is OFF, the worspace switcher work fine.

It look like the problem is in gnome composite. because using tint2 panel give same problem.

regards.

---

### Post by seeker5528 on 2010-04-22
Are you using the gconf editor to enable the compositing in Metacity or are you going to 'System --> preferences --> Appearance --> visual fx' and enabling the FX?

Turning on the FX in the appearance applet switches you from Metacity to Compiz.

Later, Seeker

---

### Post by antenna on 2010-04-22
I'm not sure this has ever worked with Compiz.  Would be nice though.

---

### Post by brambles on 2010-04-22
If you're in compiz you need to enable edge_flip_move in the Desktop Wall settings and, if I remember correctly, in the past I had to install brightside to get this to work with Metacity.

Could all have changed tho' :)

Edit:
I'm talking horsefeathers! I was thinking about dragging from one desktop to another at the edges not in the switcher

---

### Post by antenna on 2010-04-22
Yeah, there are various ways of moving windows across desktops making this only a minor complaint really, methods include:

- As mentioned above, play with the Desktop Wall/Cube settings in Compiz and you can drag them off the side.

- Use the Expo plugin in Compiz (I have mine set to activate when my mouse hits the top left screen corner), you can drag windows there in the workspace overview.

- Right click on a window title bar and select a workspace to move to.

- Set up shortcut keys in the 'Put' plugin in Compiz settings, there it allows you to set binds up for arbitrary and adjacent viewports.  I use shift + alt + num - where num is the number of the arbitrary viewport.

---

### Post by thil77 on 2010-04-23
thank for the reply to all.

I used 'System --> preferences --> Appearance --> visual fx'. So this is a compiz problem.


> making this only a minor complaint
I'm not agree with you on this subject.
Have spend many hour on tint2 to bring a clean EWMH panel.
And the result in compiz is half working software because compiz doesn't support EWMH workspace specification.

This break all 'pager' software. And for the end user could give an impression of 'unprofessional'.

As you can see, I don't like this. 
If someone have an idea how to fixed this problem, it's welcome.

---

### Post by antenna on 2010-04-23
[This bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150690") has been around a while, sounds like it's a problem with the switcher rather than Compiz perhaps.  The report mentions patches but I don't know about that..

---

### Post by thil77 on 2010-04-23
thank antenna.

will follow the bug report ... and see if I can added some technical infos.

---

