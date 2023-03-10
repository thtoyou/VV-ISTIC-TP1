# Practical Session #1: Introduction

1. Find in news sources a general public article reporting the discovery of a software bug. Describe the bug. If possible, say whether the bug is local or global and describe the failure that manifested its presence. Explain the repercussions of the bug for clients/consumers and the company or entity behind the faulty program. Speculate whether, in your opinion, testing the right scenario would have helped to discover the fault.

2. Apache Commons projects are known for the quality of their code and development practices. They use dedicated issue tracking systems to discuss and follow the evolution of bugs and new features. The following link https://issues.apache.org/jira/projects/COLLECTIONS/issues/COLLECTIONS-794?filter=doneissues points to the issues considered as solved for the Apache Commons Collections project. Among those issues find one that corresponds to a bug that has been solved. Classify the bug as local or global. Explain the bug and the solution. Did the contributors of the project add new tests to ensure that the bug is detected if it reappears in the future?

3. Netflix is famous, among other things we love, for the popularization of *Chaos Engineering*, a fault-tolerance verification technique. The company has implemented protocols to test their entire system in production by simulating faults such as a server shutdown. During these experiments they evaluate the system's capabilities of delivering content under different conditions. The technique was described in [a paper](https://arxiv.org/ftp/arxiv/papers/1702/1702.05843.pdf) published in 2016. Read the paper and briefly explain what are the concrete experiments they perform, what are the requirements for these experiments, what are the variables they observe and what are the main results they obtained. Is Netflix the only company performing these experiments? Speculate how these experiments could be carried in other organizations in terms of the kind of experiment that could be performed and the system variables to observe during the experiments.

4. [WebAssembly](https://webassembly.org/) has become the fourth official language supported by web browsers. The language was born from a joint effort of the major players in the Web. Its creators presented their design decisions and the formal specification in [a scientific paper](https://people.mpi-sws.org/~rossberg/papers/Haas,%20Rossberg,%20Schuff,%20Titzer,%20Gohman,%20Wagner,%20Zakai,%20Bastien,%20Holman%20-%20Bringing%20the%20Web%20up%20to%20Speed%20with%20WebAssembly.pdf) published in 2018. The goal of the language is to be a low level, safe and portable compilation target for the Web and other embedding environments. The authors say that it is the first industrial strength language designed with formal semantics from the start. This evidences the feasibility of constructive approaches in this area. Read the paper and explain what are the main advantages of having a formal specification for WebAssembly. In your opinion, does this mean that WebAssembly implementations should not be tested? 

5.  Shortly after the appearance of WebAssembly another paper proposed a mechanized specification of the language using Isabelle. The paper can be consulted here: https://www.cl.cam.ac.uk/~caw77/papers/mechanising-and-verifying-the-webassembly-specification.pdf. This mechanized specification complements the first formalization attempt from the paper. According to the author of this second paper, what are the main advantages of the mechanized specification? Did it help improving the original formal specification of the language? What other artifacts were derived from this mechanized specification? How did the author verify the specification? Does this new specification removes the need for testing?

## Answers

# 1.
Revue banque février 2010 - N°721
Il s’agit vraisemblablement d’un bug local, sans doute une mauvaise condition concernant la date, comme ce fût le cas pour le  Zune 30 de Microsoft. 
Le bug n’impactait que certaines cartes à puces destinées aux clients de la banque allemande ZKA, empêchant toute transaction avec un terminal bancaire.
Le fabricant des cartes impliquées, Gemalto, a réussi à apporter un correctif en attendant de fournir de nouvelles cartes corrigeant le problème.
A posteriori, s’il s’agit d’une erreur dans l’expression d’une condition sur la date, une revue de code aurait permis de la mettre en avant.

# 2.
On the appache commons-collections, PMD reported an issue about a method having 2 return statements. (search method) I would consider it a false positive since the method is relatevely simple (12 lines of code) and having a return inside the while loop increases the performance since it will stop the calculation whitout computing the whole loop. It also reported a "System.out.println()" that shoulc be replaced by a logger. I would consider this a true positive since System.out.println() is not compatible with every architecture depending on the user's program
# 3.
- L’expérience qui a était faite c’est le test de disponibilité d’un système, c’est à dire on voit l’impact
  des pannes de certains services sur la disponibilité de notre système.
  Dans ce cas, Netflix essaye de voir, si on fait échouer certain services, est ce que l’utilisateur peut toujours trouver le contenu, et aussi regarder.

- Pour faire ces expériences, il faut préciser :
 -les hypothèses
 -Les variables indépendentes
 -Les variables dépendentes
 -Le context

- NetFlix dans ces expérience elle vérifie l'évolution de la variable :
  SPS ( START PER SECOND ), par rapport au streams lancer par seconde

Il ont eu des fluctuations de la valuer de cette variable tout dépend de la période de la journée

- Plusieurs autres entreprises font ce genre d'expérience comme :
  Amazon, Google , Microsoft et Facebook

- On peut dire que Google par exemple, peut vérifier la variable : RPS ( reaserch per second )
  pour qu’il puisse savoir si l’utilisateur peut faire ces recherches et il obtient les résultats souhaités

# 4.
# 5.

