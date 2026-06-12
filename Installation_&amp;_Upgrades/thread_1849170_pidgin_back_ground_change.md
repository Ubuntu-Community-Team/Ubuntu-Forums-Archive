---
title: "pidgin back ground change"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-09-24
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

the white pidgin background was freaking me out, so i decided to "skin it" and it took me longer than 1 minute so ill make it short and sweet for you

alt + f2

gnome-terminal

run

drop this block of code in the terminal

```
cat > $HOME/.purple/gtkrc-2.0 << "EOF"
# Create a style called "inverted" where the text and base (the base color behind the widget) are the reverse of typical.
style "inverted"
{
text[NORMAL] = "#FFFFFF"
base[NORMAL] = "#000000"
}

# Apply "inverted" to conversation entry box--where you type.
widget "*pidgin_conv_entry" style "inverted"

# Apply "inverted" to conversation history pane--where you read the conversation.
widget "*pidgin_conv_imhtml" style "inverted"

widget "*pidgin_blist_treeview" style "inverted"
EOF
exit

```
press enter

and a restart of pidgin results in this....

(ps im a mad man hell bent upon world domination hence the globe wallpaper)
[IMG]http://img834.imageshack.us/img834/383/pidginskin.jpg[/IMG]

---

