---
title: "Error running mpi program after compilation"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by B.karthikeyan on 2008-06-20
I compiled my mpi program in c++ using mpic++ (openmpi) but i'm not able to run it, it gives the following error..


aravindh@Ophidian:~/Desktop/project$ mpirun -np 2 a.out < fft_data.inp
ERROR: Atleast 2 nodes required for processing...
-----------------------------------------------------------------------------
It seems that [at least] one of the processes that was started with
mpirun did not invoke MPI_INIT before quitting (it is possible that
more than one process did not invoke MPI_INIT -- mpirun was only
notified of the first one, which was on node n0).

mpirun can *only* be used with MPI programs (i.e., programs that
invoke MPI_INIT and MPI_FINALIZE).  You can use the "lamexec" program
to run non-MPI programs over the lambooted nodes.
-----------------------------------------------------------------------------


 Can somebody please help me out?!? I have to get this running in a day :(

---

