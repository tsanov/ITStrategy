---
layout: post
title:  "Case for Continuous Improvement"
ref: case-continuous-improvement
lang: en
author: "IT Strategy Team"
date: "2019-10-15"
last_modified: "2019-10-15"
---

## Summary

In The DevOps Handbook the authors make a case for teams spending at least 20% of their time towards reducing technical debt.

> The deal [between product owners and] engineering goes like this: Product management takes 20% of the team’s capacity right off the top and gives this to engineering to spend as they see fit.
> They might use it to rewrite, re-architect, or re-factor problematic parts of the code base…whatever they believe is necessary to avoid ever having to come to the team and say, ‘we need to stop and rewrite [all our code].’
> If you’re in really bad shape today, you might need to make this 30% or even more of the resources.
> However, I get nervous when I find teams that think they can get away with much less than 20%.

I am going to abstract this to suggest that all teams should spend at least 20% of their time improving the way they work.
In the case of the team I work with, we produce documentation as well as some proof of concepts to demonstrate the effectiveness of our proposed ideas.After work on day I was discussing modeling our team as an Enabling Team, from [Team Topologies](https://itrevolution.com/book/team-topologies/), with a colleague.
In the book they recommend that an enabling team could spend time assisting other teams in onboarding new technologies, or helping other teams find better ways to work.
My colleague challenged me on our ability to sell ourselves as a learning team.
People are busy, why would people want to slow themselves down by committing time away from their priorities to improve? How would you sell that to a team already working at 120% capacity?

Many of us already know from the [Phoenix Project](https://itrevolution.com/book/the-phoenix-project/) the hand wavey anecdotal justification for commiting time to improving ones process.
If one was really taken with the Phoenix Project they may invest the time to learn more by learning the magic of DevOps through books such as [The DevOps Handbook](https://itrevolution.com/book/the-devops-handbook/) (which I suggest you do).
However, if you're in a position where you need to quickly make a business case for continous improvement, how does one do this?
That is what I will try to do here.
Make a succinct argument using some simple math to demonstrate the value of continuous improvement.

### TLDR

The TLDR of this article is that 'continuous', in more formal terms, means compounding.
Or, depending on your preferred jargon, exponential.
If you graph output with the Y axis as 'units produced' and X as time, then the team that continously improves will increase their output exponentially.
And given some arbitrarily large value n (or as n approaches infinity) then exponential will always beat linear.
Given that our teams exist for some arbitrarily long time (n), then teams who continually improve will be more productive than a team who does not.

If that sounded a little math-y or jargon-y, we'll walk through it below.

## The Case for Continous Improvement

*This demonstration was created using the fantastic site, [desmos](https://www.desmos.com/calculator).*

If we graph f(x) = x we will get a line as follows

![Graph of f(x) = x]({{site.baseurl}}/assets/images/graphx.PNG)

We are defining y-axis (the vertical one) as the total units of business value produced, and the x-axis to be time.
The line then, is the total units of business value produced over some unit of time.
For the sake of this example, let's say that each increment in x is one month.

This line assums that, week after week, the team continues to do work "as usual", or the famous "we've always done it like this" approach.
With this approach, the team will (on average) produce the same units of business value each week.
If you are working over 100% this week, you will be next week too.

What's the alternative? Continuous improvement.

If we continue to improve our processes and tools week after week, we will continously improve, thereby becoming able to produce more business value over a given time.
This should give us an exponential curve, which looks something like this

<!-- markdownlint-disable MD033 -->
f(x) = x<sup>2</sup>
<!-- markdownlint-enable MD033 -->

![Graph of f(x) = x^2]({{site.baseurl}}/assets/images/drawgraphx2.PNG)

The most obvious thing we notice is that the exponential function grows much faster.
One may counter, however, that there is an initial loss in productivity if one spends time improving rather than actually *doing work*, so we must account for this.
Do do this, we must subtract some value from *f(x)* to account for the lost productivity.
For each increment in time, then, we will lose some percentage of our time.
Where x represents time, this can be written as

x * [some percentage of productivity lost]

Or, to be more succinct, we can replace [some percentage of productivity lost] with *l*.
Then we will have

x * *l*, where *l* is the amount of time spent per day on improving

With this addition, we have

<!-- markdownlint-disable MD033 -->
f(x) = x<sup>2</sup> - (x*l)
<!-- markdownlint-enable MD033 -->

What happens when we graph this? Well let's assume we spent 20% of our day on continuous improvement.
Then we lose 20% of our productivity per month.

![Graph of f(x) = x^2]({{site.baseurl}}/assets/images/graphx2minusxl.PNG)

Notice at the bottom that the curve flattens out slightly.
This decrease in productivity is always present as x (the amount of time) increases.
However, [an exponent will always beat a linear progression](https://www.khanacademy.org/math/algebra/x2f8bb11595b61c86:exponential-growth-decay/x2f8bb11595b61c86:exponential-vs-linear-growth/v/exponential-vs-linear-growth).
The next obvious step would be to then graph our "as is" way of working versus out continuous improvement method of working, and see how long it would take before a continuously improving team will take before it is more productive than the team who continues to work the same way, day after day.
Before that, however, in our previous calculation we used x^2, which is a curve that grows very quickly, and up until now, we have not justified our selection of the arbitrary value of 2.
Another way we could have written this is

<!-- markdownlint-disable MD033 -->
x<sup>2</sup> = x<sup>1+1</sup>
<!-- markdownlint-enable MD033 -->

When talking about percentage points we calculate using decimal points.
Therefore, 1 = 1.0 = 100%.
Therefore, as we had it written previously we are claiming that our productivity increases by 100% per day! If anyone has figured out how to do this, we'd love to hear from you! Unfortunately, if you live in the realm of mere mortals like me, 100% productivity increase per day is likely unattainable.

We can re-write our productivity increase function as follows

<!-- markdownlint-disable MD033 -->
f(x) = x<sup>1+[the amount of productivity increase we expect per month spent continuously improving]</sup>
<!-- markdownlint-enable MD033 -->

That's really long to say, so if we set [the amount of productivity increase we expect per month spent continuously improving] = r, then we have

<!-- markdownlint-disable MD033 -->
x<sup>2</sup> = x<sup>1+r</sup>
<!-- markdownlint-enable MD033 -->

Where r is some percentage in increased productivity.

Alright.
We're almost there! Our function for mapping how productive a continously improving team is looks something like this

<!-- markdownlint-disable MD033 -->
f(x) = x<sup>1+r</sup> - (x*l)
<!-- markdownlint-enable MD033 -->

- Where *r* is equal to the rate of improvement
- And *l* is equal to the amount of time we have spent continously improving

Next we will pick some values that make sense.
As discussed, in The DevOps Handbook they recommend %20 of your time be spent on reducing technical debt or process improvement.
So for *l* we will pick 20%, or 0.2

Now how much improvement do we expect from 20% of our time being spent on improvements? As a government employee, I know in certain cases this return can be gargantuan.
For example, [Estonia claims they save 820 years of working time annually through their use of automated digital services](https://e-estonia.com/how-save-annually-820-years-of-work/).
For our example, however, as we will see, the rate of improvement is not all that important.
You will always eventually become more productive if you continually improve for long enough.
Alright then, let's choose 10%, which is the same as 0.1.
So we are assuming for each unit of time for which you spent 20% of your time, you get half as much effecient for the time invested.
Conservative, at best.
Our function then becomes

<!-- markdownlint-disable MD033 -->
f(x) = x<sup>1+0.1</sup> - (x*.2)

f(x) = x<sup>1.1</sup> - (x*.2)
<!-- markdownlint-enable MD033 -->

And if we graph this, we will get the following curve

![f(x) = x^(1.1) - (x*l)]({{site.baseurl}}/assets/images/fullfunction.PNG)

Great! What's next? Well, let's say we compare that with a team that does not continually improve, and continues to grind through, day to day, doing things "as they've always done them".

![Compare curves]({{site.baseurl}}/assets/images/comparecurves1.PNG)

We can see that the red line, which represents the team that continually improves for 20% of their day for a small 10% return in productivity will be more productive in about 6 months (or 6.192 months, to be exact).
Even if you reduced the productivity gained by half (to 5%, or 0.05), you would still find that before 39 months is up, the team that continuously improves will inevitably end up preforming more highly than the team who does not.

We have demonstrated that even if the trade off between time invested versus potential gain is low, if one continually improves their team, over time they will become more productive than the team who does not.
Think of how long your team, or organization, has existed.
Probably many many months.
Imagine if they had started continually improving **years** ago, think about how productive they would be by now! Don't make the same mistake our predecessors did.
Start continuously improving now! Your future team members, future bosses, and your future self, will all thank you.

To satisfy the purpose of this article, one may stop here.
If you would like to play around with some numbers on desmos please click [here](https://www.desmos.com/calculator/bfk9p5ho7f).
If you're interested in further details, below we are going to talk about how to decide on the optimal trade off between productivity gained and time invested.

## A Deeper Dive

Here we're going to use a little math trickery with some basic [integration](https://www.khanacademy.org/math/integral-calculus/ic-integration/ic-integral-calc-intro/v/introduction-to-integral-calculus?modal=1) (well, basic as far as integration goes, anyways) and some discussion about how one could use [velocity](https://www.scruminc.com/velocity/) or [business value points](https://www.agilealliance.org/resources/sessions/business-value-estimation/) to refine what the ideal trade off.

Step one here is to answer the question, "well exactly how much time am I losing when I choose to invest in continuous learning?" Should I invest 20% of my time for a 10% trade off? Or would it be better to invest 30% of my time for a 20% trade off? To answer this question, we'll need to learn more about the relationships between our two curves.
More precisely, we need to know the area between the two curves.
Luckily with desmos the heavy lifting is done for us.
If you haven't already done so, click [here](https://www.desmos.com/calculator/bfk9p5ho7f) for an example.
You should see something as follows

![Area between curves]({{site.baseurl}}/assets/images/areaundercurve.PNG)

What are we seeing here? If you hover over where the two lines intercept you will see that the x value is 6.192, which is the same 6.192 you will see in the integral

![Area under curve function]({{site.baseurl}}/assets/images/integralareaundercurve.PNG)

Line 3 should read

```html
f(x) <= y <= F(x)
```

And above you should see that one line 1 and 2 we have defined f(x) and F(x), respectively, as we covered above.
The last little detail we are missing is the { x > 0 } which is specifying to only draw the line where x > 0 (to prevent the lines from going past the x-axis which adds noise to our graph).

You will also notice that in our picture of the integral is displayed a number, ~18.075.This is the area between the function f(x) and F(x).
Why is this important? This represents the size of the difference between what you would have delivered had you not started to continuously improve.
Why do we care about this? You will notice that if you increase the value of *l* (which is the time spent on improvement), that your lines now intercept at 13.786.
If you plug this back into the integral you will observe that the new area under the curve becomes 89.144.
This is of course, however, because we did not increase the rate of improvement we experience by investing another 10% of our time.
If we were to do so, we would observe that the area of the curve declines.
Click [here](https://www.desmos.com/calculator/bfk9p5ho7f) for an example.

As we covered above, however, an exponent will eventually always outgrow a linear function.
This is to say

<!-- markdownlint-disable MD033 -->
x<sup>1.1</sup> beats (x*.2) as x approaches infinty
<!-- markdownlint-enable MD033 -->

More formally we could say that as the limit of x approaches infinite, f(infinity) = infinity.

The relevant question for one here is, what is more important to your team? Being as productive as possible as quickly as possible, or is it acting in such a way that one is able to continually improve, though with the smallest possible impact on their clients and ability to produce.

_____

**Option 1**: It is more important to become as productive as possible, as quickly as possible

If this is your team, then you should opt for a situation where the team can maximize *r* as quickly as possible, even if it requires a higher time investment.

**Option 2**: Begin to continuously improve while still meeting the current expectations as best as possible.

This is where things can become a little counter intuitive.
We will see that while lowering *l* (the amount of effort put into continuous improvement), assuming *r* decreases by an equivalent amount, the area between the curves will actually increase.
To reduce the area between the curves, which represents the initial units of productivity lost when initially dedicating some percentage of our time to continuous improvement.

*The Intuitive Option*: Minimize *l* such that a small percentage of our time is dedicated to continuous learning so that we can continue to deliver on our responsibilities.

*The Better Option*: Pick the lowest value of *l* such that it maximizes the value of *r*

In the Phoenix Project the company stops all projects to focus on improving the way they work.
Following this, they are able to deliver and meet all of their deadlines and successfully deliver the previously doomed project.
How would be demonstrate that this is in fact the optimal approach to take? We already have the tools to do so above!

Because the first part of the function (x^(1+r)) grows exponentially, while the second is linear ((x*l)), it is most important to prioritize the growth of *r* than it is to invest the least amount of time possible in continuous improvement.
Let's do an example.

If we set *l* = 30% and *r* = 20%, then we will find the area between the curves, that is the total initial lost productivity, is ~6.0785

If this is your teams situation, then what is important for you is trying to find the best possible ratio is maximized between *r* and *l* (confirm [here](https://www.desmos.com/calculator/9ddu4s8fpy)).
Conversely, if we were to keep the same ration (3:2) (that is to say, the same amount of effort will result in the same amount of efficiency gain) and reduce the amount of time invested by half

- Let *l* = 15%
- Let *r* = 10%

Then we will find that the area between the curves is now ~7.7369.
In conclusion, if one is trying to mimimize the loss of productivity, it is better to invest large amounts of time and increase *r*, the rate of productivity, quickly, than it is to prioritize a low value of *l* that lowers *r*.

We are, of course, ignoring that eventually one will find that after some time, the ratio will eventually decline (that is, per unit of x spent on improving, the ROI in said investment will decline as time increases).
It is for this reason that a prolongued elevated value of *r* is likely inadvisable (though a more rigorous analysis would be helpful, and in the future it would be great to add that here).

In conclusion, if one if looking for maximum productivity it is best to maximze the value of *r*, and if one is looking to minimize the impact to their current services one should find the lowest value of *l* such that it maximizes the possible value for *r*.

_____

The next question to be answered then, would be how one would find what their *r* is given some investment *l*.
To do this, one needs metrics.

One possible option that comes to mind is the use of velocity and business value.
Velocity alone will not suffice, as given the same amount of effort by the team they should become more productive.
Therefore, while velocity remains constant (or, rather, the teams average velocity stays consistant) the amount of business value delivered should increase.
Therefore, one can measure the rate of increased productivity *r* by computing the rate of increase between the velocity and the business value.
Each sprint then, a team could calculate

```html
i = business value/velocity
```

which will give you the amount of business value produced per unit of effort required.
Week after week as you compute this value, compute the rate of change of i.
This will, over time, give you the rate at which you are improving over some interval of time.

Granted, this is assuming no significant changes in the team, and that humans, given changing circumstances, continue to give consistent evaluations throughout the process.
It's not perfect I admint, and if anyone else has any more rigious ways by which to define r, we'd love to hear from you and please submit an issue [here](https://github.com/sara-sabr/ITStrategy/issues).

In this section I have attempted to add some rigous by which we can better measure what the best approach would be for a team given their goals.
More time should be spent determining the best possible way to define *r*.

## Future Improvements

This section here acknowledges some of the points I'd like to improve, though if you would like to contribute here are to particular issues I need to revisit later.

### Problem 1: Desmos syntax

On desmos I couldn't figure out how to store the x coordinate of where the lines intercepted to store the variable in maximum value for the integral.

### Problem 2: Loss on ROI as time spent increases

Given the function

<!-- markdownlint-disable MD033 -->
f(x) = x<sup>1+*r*</sup> - x**l*
<!-- markdownlint-enable MD033 -->

As x grows there should be some function by which the exponent 1+*r* begins to reduce, as the quick wins are solved it will gradually take more effort to realize the same amount of effeciency.

## The End

Thanks for reading! This was my attempt at going from simple to more complex in an attempt to try and more formally and rigorously define the logic behind committing to continually improving.
In the first part of this document [The Case for Continous Improvement](#the-case-for-continous-improvement) I was hoping to provide a easily consumable and succinct pitch for folks to start continuously improving without requiring them to read all the books... though it would be best if they did.
It only requires one to remember a little from the dusty math books.
The second section is intended for the more committed reader to try and more deeply explore the outputs desired from continually improving, and what we should take into consideration when doing so.
This blog post was a blast to write.
I love applying the rigour math can offer to the real world, so the last section is a call out to fellow enthusiasts who would enjoy helping me dig deeper into such topics.

Thanks for reading!

## References

- [The DevOps Handbook](https://itrevolution.com/book/the-devops-handbook/)
- [Team Topologies](https://itrevolution.com/book/team-topologies/)
- [Phoenix Project](https://itrevolution.com/book/the-phoenix-project/)
- [Khan Academy](https://khanacademy.org)