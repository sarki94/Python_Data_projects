# The Anaysis

## 1. What are the most demanded skills for the top 3 most popular data roles?
 
 To find the most demanded skills for the top 3 most popular data roles. I filtered out those positins by which ones were the most popular, and got the top 5 skills for these top 3 roles. this query highlights the most popular job titles and their top skills, showing which skills i should pay attention to dependingon the role i'm targeting.

 view my notebook with detailed steps here:
 [2_Skill_Demand.ipynb](3_Project\2_Skills_Demand.ipynb)

 ###Visualize Data

```python
ig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_percent[df_skills_percent['job_title_short']== job_title].head(5)
   # df_plot.plot(kind='barh', x='job_skills', y='skill_percentage', ax=ax[i],legend=False, title=job_title)
    sns.barplot(data=df_plot, x='skill_percentage', y='job_skills', ax=ax[i], hue='skill_count', palette= 'dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel(' ')
    ax[i].set_xlabel(" ")
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)

    for n, v in enumerate(df_plot['skill_percentage']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va="center")
   
    if i != len(job_titles) - 1:
         ax[i].set_xticks([])

fig.suptitle('Likelihood of skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.2) # it fix overlab

plt.show()
```
### Results
![visualizations of top skills for data Nerds](3_Project\images\skill_demand_all_data_roles.png)

### Insights

- Python is a versatile skill, highly demanded across all the three roles, but most prominently for Data scientists (72%) and Data Enginners (65%).
- SQL is the most requested skill for Data Analsts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, python is the most sought_after skill, appering in 68% of job postings.
- Data Engineers require most specialized technical (AWS,Azura, Spark) compared to Data Analysts an d Data scientist who are expected to be proficient in more general data management and analysis tools (Excel, Tabeau).




