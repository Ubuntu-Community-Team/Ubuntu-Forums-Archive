---
title: "remove kde easily"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mick222 on 2009-10-20
I've been stupid again as usual I got curious after reading some posts on kde and decided to install it , one of the posts was about installing a separate copy to run kde and not mess up menus, I have done this before and regretted having to find everything and uninstall it.
 What i was wondering is there an easy way to remove all traces of kde or am i stuck with finding and deleting individual packages i uninstalled kubuntu desktop but this has left me with the applications in gnome. By the way it wouldn't be hard for me to reinstall if it's my best option i have a separate home partition.

---

### Post by dadedo123 on 2009-10-20
Is Kubuntu that bad? haha
I don't really know why Ubuntu makes more than one desktop environment.

---

### Post by mick222 on 2009-10-20
No i quite like it and will probably install mandriva when the new distro is released . But if you install gnome and kde together you have all the apps showing up in applications menu. Starts to look a bit like my windows used to five programs for every task.

---

### Post by Bachstelze on 2009-10-20
> **mick222 said:**
> No i quite like it and will probably install mandriva when the new distro is released . But if you install gnome and kde together you have all the apps showing up in applications menu. Starts to look a bit like my windows used to five programs for every task.

If you like KDE, why not remove just the superfluous apps? Anyway, removing kdelibs will probably remove anything KDE-related.

---

### Post by dadedo123 on 2009-10-20
Oh, when they release gnome-shell, will KDE still exist, or maybe KDE-shell? :P :S

---

### Post by mick222 on 2009-10-20
thx that will probably do it just couldn't think what else to remove. I prefer Mandriva as  kde distro like the Mcc "Mandriva control centre "very nice to use .

---

### Post by mick222 on 2009-10-20
Searched synaptic it is called kdelibs5 now
 Back to normal now "Happy days"

---

### Post by slakkie on 2009-10-20
I use the following function to remove deps of a metapackage:
```

rm-metapkg () {
        local i
        for i in $*
        do
                sudo aptitude remove $i
                sudo aptitude markauto $(apt-cache depends $1 | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | awk '{print $NF}')
        done
        [ -n "$i" ] && purge_pkg
}

```

It might leave some packages, since I tested it with the ubuntu-desktop package, but that is because of the dependency of a dependency. Maybe I should look into that as well :)

---

