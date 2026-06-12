---
title: "HOWTO set back the previous ctrl-alt-del behaviour"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hexion on 2008-10-19
In hardy, when you press the combination ctrl-alt-del the "shutdown" menu appears.

That changed in intrepid, now the "close-change session" menu appears.

To go back to the previous behaviour, you need to do the following:

- Open System / Preferences / Keyboard Shortcuts
- Disable the combination ctrl-alt-del for the option "End session" by clicking once on that option and then pressing backspace.
- Open gconf-editor via terminal or with alt-f2
- Go to apps / metacity / global_keybindings
- Change the value for "run_command_9" to "<Control><Alt>Delete" without quotes
- Go to apps / metacity / keybinding_commands
- Change the value for "command_9" to "gnome-session-save --shutdown-dialog" without quotes

That's it. Enjoy ;)

---

