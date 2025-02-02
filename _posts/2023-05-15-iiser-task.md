---
title: 'Trying LLMs on Google QED'
date: 2023-05-15
permalink: /posts/first-task-llms/
tags:
  - GPT
  - QAE
  - Prompt Engineering
---

This is a part of the preliminary work carried out during the IISER Summer Student Research Program in 2023. Feel free to reach out if you have any questions!

{: .notice--warning}
This page is under development :D
{: .notice--warning}

* Any pre-requisites?
  * It will be great if you can watch the online lectures of [ChatGPT Prompt Engineering for Developers](https://www.deeplearning.ai/short-courses/chatgpt-prompt-engineering-for-developers/) by Andrew NG (Around 9 tutorials will be available)
  * An OpenAI account (a free account would do for testing! Generate an API key)

So, what's QED ❓
======
Simply, it's a framework for explaining answers in question answering. It involves sentence selection, referential equality and predicate entailment. The dataset consists of examples with annotations, including *question, paragraph, answer and explanations*.
 
What are we trying to do? 🤔
======
Via this experiment, we are trying to assess the effectiveness of GPT in Question, Answer and reasoning tasks.

Let's get started with the 1st sub-task 🤝
------
Given a \\((q, c, a)\\) triple, we have to make a prediction \\(\hat{e} = f(q, c, a)\\),  
where \\(q\\) refers to the question, \\(c\\) refers to the context, \\(a\\) refers to the answer  
and \\(f\\) is the function that maps the tuple to an `explanation`.
We might, for example, define:

$$
f(q, c, a) = \arg\max_e p(e \mid q, c, a; \theta)
$$

under some model \\(p(\dots)\\).  

The evaluation measure is then given by:

$$
\frac{1}{|\varepsilon|} \sum_{(q,c,a,e) \in \varepsilon} l_1(e, f(q, c, a))
$$

where \\(l_1(e, \hat{e})\\) is a per-example evaluation measure indicating how close \\(\hat{e}\\) is to \\(e\\).

Basically, this is an **explanation generation** task!
