To: Michal Januszewski <mjanusz@google.com>
CC: Plaza, Stephen <plazas@janelia.hhmi.org>
Re: Fragmented neuron examples

Hi Michal,
 
I’m proceeding with the following plan.
 
In the text below:
“old” agglo means final_20180312_32nm_16nm_all_cbs32_upto10_cb16_upto10_freeze_all ,
“proposed” agglo means final_20180312_32nm_16nm_all_cbs32_upto10_cb16_upto10_freeze_all_upd0408_v2, and
“patched” agglo is the combination of the two, as produced by this procedure.
 
I’m keeping most new bodies from your proposed agglomeration, except:
(1) I’m rejecting splits of bodies that we’ve already reviewed and
(2) I’m rejecting any proposed bodies which contain any part of an “old” body that we already reviewed.
 
After that, I’m removing all “phantom” supervoxels (i.e. supervoxels which do not exist in the volume), which fall into three sets:
(1) You suggested “renames” for the 24 large ones, so I’m applying those renames.
(2) For the smaller ones, I’m renaming them with one of their neighbors.
(3) If they have not “real” neighbors (only other phantoms), I’m simply removing them (there are 7).
 
After that, I’m applying the 229 merges you provided to fix continuity errors that introduced when our splits were applied (aux_merges_split_bodies_continuity.csv) using score=0.
 
Once that’s complete, I’ll send you my patched merge graph.  Do you think you’ll be able to use it as a starting point for re-running your “speculative” merge computation?  Also, is there any chance you’d be able to produe a BrainMaps version of the patched volume, for viewing in Neuroglancer?
 
> if there is anything I should keep in mind to make this easier in the future
 
Not much comes to mind, but I wonder if maybe we should be sharing our analysis code.  If we need to make further “patches” to the graph, perhaps we can discuss what we think the impact will be, and how we arrived at those conclusions.  (If you’re interested in the code I’m running to generate this patched version, I can share that with you.)
 
Best,
Stuart
