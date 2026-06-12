---
title: "GPU temps not shown in sensor ring screenlet"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jhan1 on 2009-04-22
I have upgraded to jaunty and notice that my sensor ring screenlet that

used to show gpu temperature in Intrepid no longer works.  The option

for a gpu temp is not even listed anymore in the config.  I also tried

the Nvidia screenlet but it will not even open.  The gpu temp is listed 

in the Nvidia x server settings thermal monitor however.


  I like to view this info on my desktop at all times so does anyone know

of any other program or widget that will work in Jaunty.  Thanks

---

### Post by dabl on 2009-04-22
gkrellm works fine here. You might need to re-run > sudo sensors-detect

---

### Post by jhan1 on 2009-04-22
> **dabl said:**
> gkrellm works fine here. You might need to re-run

Thanks,  I installed gkrellm and configured it to my needs.  Works great!!!

---

